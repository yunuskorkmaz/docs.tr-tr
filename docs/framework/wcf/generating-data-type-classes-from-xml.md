---
title: XML'den Veri Türü Sınıfları Oluşturma
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 6b38a0aea3101c70b3c3ec0c8feb4ee88018b64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="generating-data-type-classes-from-xml"></a>XML'den Veri Türü Sınıfları Oluşturma
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir. Bu konu, veri türleri .NET Blog RSS akışı için otomatik olarak oluşturmayı açıklar.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>.NET Blog RSS XML alma akış  
  
1.  Internet Explorer'a gidin [.NET Blog RSS akışı](https://blogs.msdn.microsoft.com/dotnet/feed/).  
  
2.  Sayfanın sağ tıklatıp **kaynağı görüntüle**.  
  
3.  Akışın metni tuşlarına basarak kopyalayın **Ctrl + A** tüm metni seçmek için ve **Ctrl + C** kopyalamak için.  
  
### <a name="creating-the-data-types"></a>Veri türleri oluşturma  
  
1.  Kullanılacak proxy olduğu bir kod dosyasını açın. Bu dosya parçası olması gereken bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projesi.  
  
2.  İmleci dosyası var olan tüm sınıflar dışında bir konuma yerleştirin.  
  
3.  Seçin **Düzenle**, **Özel Yapıştır**, **XML sınıflar Yapıştır**.  
  
4.  Adlı sınıf `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` ve `rssChannelItemGuid` RSS akışı öğelerinde erişmek için gerekli üyelerle oluşturulur.  
  
### <a name="using-the-generated-classes"></a>Oluşturulan sınıflarını kullanma  
  
1.  Sınıflar sonra diğer sınıflar gibi kodda kullanılabilir. Aşağıdaki kod örneğinde yeni bir örneğini döndürür `rssChannelImage` sınıfı.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
