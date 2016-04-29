<h1>Botones de compartir en redes sociales y botón de siguiente post para versión móvil de tu sitio con WordPress.</h1> 

No soy muy fan de usar plugins, por esta razón decido implementar mis códigos en mi sitio web, esto me ayuda a poder tener libertar de modificaciones y al mismo tiempo evito consumir recursos al tener muchos plugins. 

<h2>Instalación.</h2>

1.- Encuentra el archivo de estilo de tu tema, por lo regular se encuentra en la siguiente ruta "/wp-content/themes/nombre-de-tu-tema" con el nombre de style.css.
<br><br>
2.- Coloca el siguiente código al final del archivo:<br>
<code>
.flex-container{  
	display: none;
}
@media only screen  and (max-width: 600px) { 
	.flex-container {
	    display: -webkit-flex;
	    display: flex; 
	    position:fixed;
	    bottom:0; 
	    z-index:999999;
	    width: 100%;
	}
    .flex-itemf, .flex-itemt{
    	width: 25%;
    	padding: 10px;
    	color: white;
    	text-align: center;
    	font-size: 15px;
    }	
	.flex-itemf {
	    background-color: #3b5998; 
	}
	.flex-itemt{
		background: #00aced;
	}
	.flex-items{
		background: #E6E6E6;
		width: 50%;
		padding: 10px;
    	color: white;
    	text-align: center;
    	font-size: 15px;
	}

	.flex-items a{
		color: #6E6E6E;
	}
}
</code>
<br><br>
3.- Encuentra el archivo single.php en la misma ruta "/wp-content/themes/nombre-de-tu-tema" y coloca lo siguiente al final del mismo:<br>
<code>
<div class="flex-container">
    <div class="flex-itemf">
	   <a style="color:white;" href="https://www.facebook.com/sharer/sharer.php?u=<?php echo the_permalink(); ?>" title="Compartir en Facebook" target="_blank">
	        <i class="fa fa-facebook"></i>
	    </a>
	</div>
	<div class="flex-itemt">
	    <a style="color:white;" href="https://twitter.com/intent/tweet?text=<?php echo the_title(); ?>&url=<?php echo the_permalink();?>" title="Compartir en Twitter" target="_blank">
	        <i class="fa fa-twitter"></i>
	    </a>
	</div> 
	<div class="flex-items">
		<?php if (strlen(get_next_post()->post_title) > 0) { ?>
        <?php next_post_link( '%link', 'SIGUIENTE <i class="fa fa-chevron-right"></i>'); ?>
        <?php } else { ?>
        <?php previous_post_link( '%link', '<i class="fa fa-chevron-left"></i> ANTERIOR'); ?>    
        <?php }?>
	</div>         
</div>
</code>
<br><br>
4.- Guarda cambios.
<br><br>
Listo, ya tendrás los botones que vemos en la imagen de arriba. Cuanto exista un siguiente post saldrá la opción “Siguiente”, en caso de que no existe saldrá la opción de “Anterior”.
<br><br>
Cualquier duda estoy en Twitter:  @Angeel_Sancheez

