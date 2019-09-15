---
title: XML'den Veri Türü Sınıfları Oluşturma
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: bf5596211e78842153b7406273626a7fa3c3aeea
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990281"
---
# <a name="generating-data-type-classes-from-xml"></a>XML'den Veri Türü Sınıfları Oluşturma
.NET Framework 4,5, XML 'den veri türü sınıfları oluşturmak için yeni bir özellik içerir. Bu konu başlığında, .NET blog RSS akışı için otomatik olarak veri türleri oluşturma açıklanır.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>.NET blog RSS akışından XML edinme  
  
1. Internet Explorer 'da [.net blog RSS akışına](https://devblogs.microsoft.com/dotnet/feed/)gidin.  
  
2. Sayfaya sağ tıklayın ve **kaynağı görüntüle**' yi seçin.  
  
3. Tüm metni seçmek için **CTRL + A** tuşlarına basarak akışın metnini kopyalayın ve kopyalamak için **CTRL + C** ' ye basın.  
  
### <a name="creating-the-data-types"></a>Veri türleri oluşturma  
  
1. Proxy 'nin kullanılacağı bir kod dosyası açın. Bu dosya .NET Framework 4,5 projesinin bir parçası olmalıdır.  
  
2. İmleci dosyadaki bir konuma var olan sınıfların dışında yerleştir.  
  
3. **Düzenle**, **Özel Yapıştır**, **XML 'i sınıflar olarak Yapıştır**' ı seçin.  
  
4. ,, `link`, `rss` `rssChannel` `rssChannelImage`Ve adlı`rssChannelItemGuid` sınıflar, RSS akışındaki öğelere erişmek için gerekli üyelerle birlikte oluşturulur. `rssChannelItem`  
  
### <a name="using-the-generated-classes"></a>Oluşturulan sınıfları kullanma  
  
1. Sınıflar oluşturulduktan sonra, diğer sınıflar gibi kodda kullanılabilirler. Aşağıdaki kod örneği, `rssChannelImage` sınıfının yeni bir örneğini döndürür.  
  
    ```csharp  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
