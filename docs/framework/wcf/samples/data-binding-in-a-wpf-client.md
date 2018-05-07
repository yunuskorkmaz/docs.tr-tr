---
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 225bdedb67e218092ff3369d4fe742c4fc897fc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Windows Presentation Foundation İstemcisinde Veri Bağlama
Bu örnek bir Windows Presentation Foundation (WPF) istemcisinde veri bağlama kullanımını göstermektedir. Örnek rasgele bir dizi istemciye döndürülecek albümleri oluşturur bir Windows Communication Foundation (WCF) hizmetini kullanır. Her albüm bir ad, bir fiyat ve albüm parçaları listesini içerir. Albüm parçaları bir ad ve süresi vardır. Hizmet tarafından döndürülen bilgilerin otomatik olarak Windows Presentation Foundation (WPF) istemci tarafından sağlanan kullanıcı arabirimi (UI) bağlıdır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Veri bağlama otomatik olarak bir kullanıcı Arabirimi bağlanması için bir veri kaynağı sağlar. Program aracılığıyla her kullanıcı Arabirimi öğesi bir veri nesnesi ya da veri nesnelerinin bir dizisi verilerle güncelleştirme olduğunu gerektirmediği için bu programlama modeli kolaylaştırır. Tek bir kullanıcı Arabirimi öğesi veya birden çok girişi gibi alan bir denetim için bir dizi nesneyi bağlayabileceğiniz bir `ListBox`. Aşağıdaki kod için verinin nasıl bağlanacağını gösterir `DataContext` bir kullanıcı Arabirimi öğesi.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 Önceki örnekte, `DataContext` için `grid` adlı Düzen öğesi `myPanel` tarafından döndürülen veri kümesi `GetAlbumList` yöntemi. `DataContext` Kendi üst öğeler bağlama yolu gibi diğer özelliklerini yanı sıra, bağlama için kullanılan veri kaynağı hakkında bilgi devralınacak öğeleri sağlar. Sunucu üzerindeki veriler her güncelleştirildiğinde kod satırı yürütülmelidir. Örneğin, pencerenin başlatıldığında ve yeni albümü eklendiğinde yürütülür.  
  
 Aşağıdaki örnek XAML kodda `ListBox` belirtir `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Bu, en üst düzey kullanıcı Arabirimi öğesi veriye de bu denetim (diğer bir deyişle, Albümler dizi) bağlı belirtir. Ayrıca, `ItemTemplate="{StaticResource AlbumStyle}"` her öğe için kullanılacak veri şablonu belirtir `ListBox`. Verileri nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz. Şablonları uygulamadaki diğer kullanıcı Arabirimi öğeleri için yeniden kullanılabilir, bu veri avantajı veri şablonu tanımlanan ve tek bir yerde tutulan var.  
  
 `AlbumStyle` Veri şablonu yerleştirir iki içeren bir kılavuz çıkışı `TextBlock`s yan yana. Bir albüm albüm ve diğer parçaları sayısı adını belirtir.  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 İkinci bir aşağıdaki XAML kodu oluşturur `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kod için bir yol belirtir `ItemsSource`. Bu veri bu denetime bağlı değil en üst düzey veri ancak üst düzey veri adlı bir özelliği olduğunu gösterir `Tracks`. Bu özellik, albüm içinde yer alan parçaları dizisi temsil eder. Ayrıca, farklı bir `DataTemplate` adlı `TrackStyle` belirtilir. Düzenini `TrackStyle` şablonu benzer olarak `AlbumStyle` şablonu, ancak `TextBlock`s farklı özelliklerine bağlıdır. Bu durum, iki şablonları farklı veri nesneleriyle kullanılır çünkü.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a>Ayrıca Bkz.
