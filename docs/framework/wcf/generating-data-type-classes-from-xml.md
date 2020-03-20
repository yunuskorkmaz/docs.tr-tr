---
title: XML'den Veri Türü Sınıfları Oluşturma
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184128"
---
# <a name="generating-data-type-classes-from-xml"></a>XML'den Veri Türü Sınıfları Oluşturma
.NET Framework 4.5, XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir. Bu konu, .NET Blog RSS akışı için veri türlerinin otomatik olarak nasıl üretilebildiğini açıklar.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>.NET Blog RSS akışından XML alma  
  
1. Internet Explorer'da [,.NET Blog RSS akışına](https://devblogs.microsoft.com/dotnet/feed/)gidin.  
  
2. Sayfaya sağ tıklayın ve **Kaynağı Görüntüle'yi**seçin.  
  
3. Tüm metni seçmek için **Ctrl+A** tuşuna basarak özet akışının metnini ve kopyalamak için **Ctrl+C'yi** kopyalayın.  
  
### <a name="creating-the-data-types"></a>Veri türlerini oluşturma  
  
1. Proxy'nin kullanılacağı bir kod dosyası açın. Bu dosya bir .NET Framework 4.5 projesinin bir parçası olmalıdır.  
  
2. İmleci dosyadaki bir konuma varolan sınıfların dışına yerleştirin.  
  
3. Sınıf olarak **Yap,** **Yapıştır Özel**, **Yapıştır XML'i seçin.**  
  
4. , `link`, `rss` `rssChannel`, `rssChannelImage` `rssChannelItem` , `rssChannelItemGuid` adlı sınıflar ve RSS akışındaki öğelere erişmek için gerekli üyelerle oluşturulur.  
  
### <a name="using-the-generated-classes"></a>Oluşturulan sınıfları kullanma  
  
1. Sınıflar oluşturulduktan sonra, diğer sınıflar gibi kod olarak kullanılabilir. Aşağıdaki kod örneği sınıfın yeni `rssChannelImage` bir örneğini döndürür.  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
