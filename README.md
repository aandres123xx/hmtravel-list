<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista di Attesa</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .waiting-list-container {
            background-color: #fff;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.1);
            width: 400px;
            max-height: 80vh;
            overflow-y: auto;
        }

        h1 {
            font-size: 24px;
            text-align: center;
            margin-bottom: 20px;
        }

        .waiting-list {
            list-style-type: none;
            padding: 0;
        }

        .waiting-list li {
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }

        .footer {
            text-align: center;
            margin-top: 20px;
            font-size: 14px;
            color: #555;
        }
    </style>
</head>
<body>

    <div class="waiting-list-container">
        <h1>Lista di Attesa</h1>

        <ul class="waiting-list" id="waiting-list-ul">
            <!-- La lista si popolerà dinamicamente -->
        </ul>

        <div class="footer">
            <p><a href="index.html">Torna alla pagina principale</a></p>
        </div>
    </div>

    <script>
        // Funzione per ottenere la lista di attesa dal localStorage
        function getWaitingList() {
            return JSON.parse(localStorage.getItem('waitingList')) || [];
        }

        // Funzione per aggiornare la lista nella pagina
        function updateWaitingList() {
            const list = getWaitingList();
            const waitingListUl = document.getElementById('waiting-list-ul');
            waitingListUl.innerHTML = '';  // Svuota la lista prima di aggiornarla

            if (list.length === 0) {
                waitingListUl.innerHTML = '<li>No data available</li>';
            } else {
                list.forEach((item, index) => {
                    const li = document.createElement('li');
                    li.textContent = `${index + 1}. ${item.cognome} - ${item.destinazione}`;
                    waitingListUl.appendChild(li);
                });
            }
        }

        // Carica la lista quando la pagina è pronta
        window.onload = updateWaitingList;
    </script>

</body>
</html>
