---
title: Windows Presentation Foundation İstemcisinde Veri Bağlama
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183815"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Windows Presentation Foundation İstemcisinde Veri Bağlama
Bu örnek, bir Windows Sunu Temeli (WPF) istemcisinde veri bağlama kullanımını göstermektedir. Örnek, istemciye dönmek için rasgele bir dizi albüm oluşturan bir Windows Communication Foundation (WCF) hizmetini kullanır. Her albümün bir adı, bir fiyatı ve albüm parçalarının bir listesi vardır. Albüm parçalarının bir adı ve süresi var. Hizmet tarafından döndürülen bilgiler, Windows Sunu Temeli (WPF) istemcisi tarafından sağlanan kullanıcı arabirimine (UI) otomatik olarak bağlanır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Veri bağlama, bir veri kaynağının otomatik olarak kullanıcı arasına bağlanmasını sağlar. Bu, her kullanıcı arabirimi öğesini bir veri nesnesinden veya bir veri nesnesi dizisinden gelen verilerle programlı bir şekilde güncelleştirmenizi gerektirmediği için programlama modelini basitleştirir. Bir nesneyi tek bir UI öğesine veya diziye `ListBox`bağlayabilirsiniz. Aşağıdaki kod, verileri bir Web-Posta öğesine nasıl bağlanınca `DataContext` gösterir.  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 `DataContext` Önceki örnekte, `grid` adlı `myPanel` düzen öğesi `GetAlbumList` yöntem tarafından döndürülen verilere ayarlanır. Öğelerin `DataContext` bağlama için kullanılan veri kaynağı hakkında üst öğelerinden bilgileri ve yol gibi bağlamanın diğer özelliklerini devralmasına olanak tanır. Kod satırı, sunucudaki veriler her güncelleştirilince yürütülmelidir. Örneğin, pencere başharfe geçtiğinde ve yeni bir albüm eklendiğinde yürütülür.  
  
 Aşağıdaki örnekxAML kodunda, `ListBox` `ItemsSource="{Binding }"`belirtir.  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Bu, üst düzey Web Bilgisi öğesine bağlı verilerin de bu denetime (diğer bir şekilde Albümler dizisine) bağlı olduğunu belirtir. Buna ek `ItemTemplate="{StaticResource AlbumStyle}"` olarak, her öğe için kullanılacak veri `ListBox`şablonu belirtir. Verilerin nasıl biçimlendirilmesi gerektiğini belirtmek için veri şablonları da tanımlayabilirsiniz. Bu veri şablonları uygulamadaki diğer Kullanıcı Arabirimi öğeleri için yeniden kullanılabilir, avantajı veri şablonu tanımlanır ve tek bir yerde korunur.  
  
 Veri `AlbumStyle` şablonu yan yana iki `TextBlock`s ile bir ızgara ortaya koyar. Biri Albümün adını, diğeri ise albümdeki Parça sayısını belirtir.  
  
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
  
 Aşağıdaki XAML kodu ikinci `ListBox`bir oluşturur.  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 Kod için bir yol `ItemsSource`belirtir. Bu, bu denetime bağlı verilerin üst düzey veriler değil, adı geçen `Tracks`üst düzey verilerin bir özelliği olduğunu gösterir. Bu özellik, albüm içinde bulunan parça dizisini temsil eder. Buna ek olarak, farklı `DataTemplate` bir adlandırılmış `TrackStyle` belirtilir. `TrackStyle` Şablonun düzeni `AlbumStyle` şablonunkine benzer, ancak `TextBlock`s farklı özelliklere bağlıdır. Bunun nedeni, iki şablonun farklı veri nesneleri ile kullanılmasıdır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
