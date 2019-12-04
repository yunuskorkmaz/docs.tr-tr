---
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 44a208cf081ef00396dfc874349dff57363c0df3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715393"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Windows Presentation Foundation İstemcisinde Veri Bağlama
Bu örnek, bir Windows Presentation Foundation (WPF) istemcisinde veri bağlamanın kullanımını gösterir. Örnek, istemciye dönmek için bir albüm dizisini rastgele üreten bir Windows Communication Foundation (WCF) hizmetini kullanır. Her albümün bir adı, fiyatı ve albüm izlemelerinin bir listesi vardır. Albüm izlemelerinin adı ve süresi vardır. Hizmet tarafından döndürülen bilgiler, Windows Presentation Foundation (WPF) istemcisi tarafından verilen kullanıcı arabirimine (UI) otomatik olarak bağlanır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Veri bağlama bir veri kaynağının bir kullanıcı arabirimine otomatik olarak bağlanmasını sağlar. Bu, programlama modelini basitleştiğinden, her UI öğesini bir veri nesnesinden veya bir dizi veri nesnesinden verilerle programlı bir şekilde güncelleştirmenizi gerektirmez. Bir nesneyi tek bir UI öğesine veya bir diziye, `ListBox`gibi birden çok girişi alan bir denetime bağlayabilirsiniz. Aşağıdaki kod, bir kullanıcı arabirimi öğesinin `DataContext` nasıl veri bağlanacağını gösterir.  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 Önceki örnekte, `myPanel` adlı `grid` düzen öğesi için `DataContext` `GetAlbumList` metodu tarafından döndürülen verilere ayarlanır. `DataContext`, öğelerin bağlama için kullanılan veri kaynağı ve yol gibi bağlamanın diğer özellikleri hakkında üst öğelerinden bilgi devralmasını sağlar. Sunucudaki verilerin her güncelleştirildiği her seferinde kod satırının yürütülmesi gerekir. Örneğin, pencere başlatıldığında ve yeni bir albüm eklendiğinde yürütülür.  
  
 Aşağıdaki örnek XAML kodunda, `ListBox` `ItemsSource="{Binding }"`belirtir.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Bu, üst düzey UI öğesine bağlanan verilerin de bu denetime (yani Albümler dizisi) bağlandığını belirtir. Ayrıca, `ItemTemplate="{StaticResource AlbumStyle}"` `ListBox`her öğe için kullanılacak veri şablonunu belirtir. Verilerin nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz. Bu veri şablonları, uygulamadaki diğer kullanıcı arabirimi öğeleri için yeniden kullanılabilir. avantajı, veri şablonunun tek bir yerde tanımlanması ve saklanması olabilir.  
  
 `AlbumStyle` veri şablonu iki `TextBlock`yan yana bir kılavuz yerleştirir. Bir tane, albümün adını ve albümdeki diğer parça sayısını belirtir.  
  
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
  
 Aşağıdaki XAML kodu ikinci bir `ListBox`oluşturur.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kod `ItemsSource`için bir yol belirtir. Bu, bu denetime bağlanan verilerin en üst düzey veriler olmadığını, `Tracks`adlı en üst düzey verilerin bir özelliğini olduğunu gösterir. Bu özellik, albümün içindeki izlemelerin dizisini temsil eder. Ayrıca, `TrackStyle` adlı farklı bir `DataTemplate` belirtilir. `TrackStyle` şablonun düzeni `AlbumStyle` şablonuyla benzerdir, ancak `TextBlock`s farklı özelliklere bağlanır. Bunun nedeni, iki şablonun farklı veri nesneleriyle kullanıllarıdır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
