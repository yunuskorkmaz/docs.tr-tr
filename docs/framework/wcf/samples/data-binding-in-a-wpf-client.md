---
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 1bc6dd2ef981115068cbd4cd491a14fea70d7e3a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305448"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Windows Presentation Foundation İstemcisinde Veri Bağlama
Bu örnek, bir Windows Presentation Foundation (WPF) istemcisinde veri bağlama kullanımını gösterir. Örnek, rastgele albümleri istemciye döndürmek için bir dizi oluşturur. bir Windows Communication Foundation (WCF) hizmeti kullanır. Bir ad ve fiyat albüm parçaları listesini her albüm sahiptir. Albüm parçaları bir ad ve süresi vardır. Hizmet tarafından döndürülen bilgileri otomatik olarak Windows Presentation Foundation (WPF) istemci tarafından sağlanan kullanıcı arabirimi (UI) bağlıdır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Veri bağlama, bir veri kaynağı için bir kullanıcı Arabirimi otomatik olarak bağlı olmasını sağlar. Program aracılığıyla her UI öğesi bir veri nesnesi ya da veri nesnelerinin bir dizisi verilerle güncelleştirmeniz gerekmez çünkü bu bir programlama modeli kolaylaştırır. Tek bir kullanıcı Arabirimi öğesi veya bir dizi gibi birden fazla giriş alan bir denetim için bir nesne adlarınıza bağlayabileceğiniz bir `ListBox`. Aşağıdaki kod, verilere bağlama işlemi gösterilmektedir `DataContext` UI öğesi.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 Önceki örnekte, `DataContext` için `grid` adlı Düzen öğesi `myPanel` tarafından döndürülen veriler için ayarlanmış `GetAlbumList` yöntemi. `DataContext` Kendi bağlamanın yolu gibi diğer özellikleri yanı sıra, bağlama için kullanılan veri kaynağı hakkında üst öğelerden bilgi öğelerin izin verir. Sunucudaki veriler her güncelleştirildiğinde, kod satırının yürütülmelidir. Örneğin, pencerenin başlatıldığında ve yeni albümü eklendiğinde yürütülür.  
  
 Aşağıdaki örnek kodda XAML, `ListBox` belirtir `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Bu, en üst düzey bir kullanıcı Arabirimi öğesi için veriye bu denetimin (diğer bir deyişle, Albümler dizisi) bağlı olduğu belirtir. Ayrıca, `ItemTemplate="{StaticResource AlbumStyle}"` her öğe için kullanılacak veri şablonu belirtir `ListBox`. Ayrıca, verileri nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz. Uygulamadaki diğer kullanıcı Arabirimi öğeleri için şablonlar yeniden Bu avantajı veri şablonunun tanımlanır ve tek bir yerde tutulan verilerdir.  
  
 `AlbumStyle` İki içeren bir kılavuz düzenlediğinden veri şablonu `TextBlock`yan yana s. Bir albümü adını albüm ve diğer iz sayısını belirtir.  
  
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
  
 İkinci aşağıdaki XAML kodu oluşturur `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kod için bir yol belirtir `ItemsSource`. Bu denetimin veriye değil en üst düzey veri ancak bir özelliğidir; adlı en üst düzey veri olduğunu gösterir `Tracks`. Bu özellik, parçaları albümü içinde yer alan dizi temsil eder. Ayrıca, farklı bir `DataTemplate` adlı `TrackStyle` belirtilir. Düzenini `TrackStyle` şablonudur benzer `AlbumStyle` şablonu, ancak `TextBlock`s farklı özelliklerine bağlıdır. Bu durum, iki şablonları, farklı veri nesneleriyle kullanılır çünkü.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
