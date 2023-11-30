# PhpMySQL2MySQLi
PHP MySQL to MySQLi patch  
 
$mysqli = null; // Lien global vers la connexion MySQLi  

// Fonction mysql_connect    
function mysql_connect($serveur, $utilisateur, $motDePasse, $baseDeDonnees) {   
    global $mysqli;  
    $mysqli = mysqli_connect($serveur, $utilisateur, $motDePasse, $baseDeDonnees);  
    if (!$mysqli) {  
        die("La connexion a échoué : " . mysqli_connect_error());  
    }  
    return $mysqli;  
}  
 
// Fonction mysql_query  
function mysql_query($requete) {  
    global $mysqli;  
    $resultat = mysqli_query($mysqli, $requete);  
    if (!$resultat) {  
        die("La requête a échoué : " . mysqli_error($mysqli));  
    }  
    return $resultat;  
}  
 
// Fonction mysql_num_rows  
function mysql_num_rows($resultat) {  
    global $mysqli;  
    $nombre_de_lignes = mysqli_num_rows($resultat);  
    return $nombre_de_lignes;  
}  
 
// Fonction mysql_fetch_array  
function mysql_fetch_array($resultat, $type = MYSQLI_BOTH) {  
    global $mysqli;  
    $ligne = mysqli_fetch_array($resultat, $type);  
    return $ligne;  
}  
 
// Fonction mysql_fetch_assoc  
function mysql_fetch_assoc($resultat) {  
    global $mysqli;  
    $ligne_assoc = mysqli_fetch_assoc($resultat);  
    return $ligne_assoc;  
}  
 
// Fonction mysql_fetch_row  
function mysql_fetch_row($resultat) {  
    global $mysqli;  
    $ligne_row = mysqli_fetch_row($resultat);  
    return $ligne_row;  
}  
 
// Fonction mysql_fetch_object  
function mysql_fetch_object($resultat, $classe = 'stdClass', array $arguments = null) {  
    global $mysqli;  
    $objet = mysqli_fetch_object($resultat, $classe, $arguments);  
    return $objet;  
}  
 
// Fonction mysql_insert_id  
function mysql_insert_id() {  
    global $mysqli;  
    $id_insere = mysqli_insert_id($mysqli);  
    return $id_insere;  
}   
 
// Fonction mysql_affected_rows  
function mysql_affected_rows() {  
    global $mysqli;  
    $nombre_de_lignes_affected = mysqli_affected_rows($mysqli);  
    return $nombre_de_lignes_affected;  
}  
 
// Fonction mysql_real_escape_string  
function mysql_real_escape_string($string) {  
    global $mysqli;  
    $escaped_string = mysqli_real_escape_string($mysqli, $string);  
    return $escaped_string;  
} 
