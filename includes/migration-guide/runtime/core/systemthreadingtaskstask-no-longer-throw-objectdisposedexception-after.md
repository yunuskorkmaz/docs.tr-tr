### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task nesne kullanıldıktan sonra ObjectDisposedException artık throw

|   |   |
|---|---|
|Ayrıntılar|Dışında <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=name> yöntemleri artık throw bir <xref:System.ObjectDisposedException?displayProperty=name> nesne kullanıldıktan sonra özel durum. Bu değişiklik, önbelleğe alınan görevleri kullanımını destekler. Örneğin, bir yöntem yeni bir görev ayırmak yerine zaten tamamlanmış bir işlemi temsil etmek için önbelleğe alınmış bir görevi döndürebilir. Herhangi bir görev kullanıcısı bunu atabildiğinden ve bu da onu kullanışsız hale getirdiğinden, bu önceki .NET Framework sürümlerinde mümkün değildi.|
|Öneri|Görev yöntemleri artık atabilir unutmayın <xref:System.ObjectDisposedException?displayProperty=name> durumlarda nesne atıldı. Bir uygulama bir görev atıldı öğrenmek için bu özel durum bağlı değilse, bunu açıkça görev durumunu denetlemek için güncelleştirilmelidir kullanarak <xref:System.Threading.Tasks.Task.Status>.|
|Kapsam|Küçük|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

