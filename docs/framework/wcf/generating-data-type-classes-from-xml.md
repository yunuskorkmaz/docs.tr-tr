---
title: XML'den Veri Türü Sınıfları Oluşturma
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: b99bb40105398dbd91b910c4a19828d069c3d9e7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380215"
---
# <a name="generating-data-type-classes-from-xml"></a>XML'den Veri Türü Sınıfları Oluşturma
.NET framework 4.5, XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir. Bu konuda, veri türleri .NET blogu RSS akışı için otomatik olarak oluşturacak şekilde açıklar.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>XML alma .NET blogu RSS akışı  
  
1. Internet Explorer'da gidin [.NET blogu RSS akışı](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Sayfanın sağ tıklayıp **kaynağı görüntüle**.  
  
3. Akışın metni tuşlarına basarak kopyalayın **Ctrl + A** tüm metni seçmek için ve **Ctrl + C** kopyalanacak.  
  
### <a name="creating-the-data-types"></a>Veri türleri oluşturma  
  
1. Kullanılacak proxy olduğu bir kod dosyası açın. Bu dosya, .NET Framework 4.5 projesinin bir parçası olmalıdır.  
  
2. Dosyanın mevcut tüm sınıflar dışında bir konumda imleci yerleştirin.  
  
3. Seçin **Düzenle**, **Özel Yapıştır**, **XML sınıflar Yapıştır**.  
  
4. Sınıflar adlandırılan `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` ve `rssChannelItemGuid` RSS akışı öğeleri erişmek için gereken üyeleri ile oluşturulur.  
  
### <a name="using-the-generated-classes"></a>Oluşturulan sınıfları kullanma  
  
1. Sınıfları oluşturduktan sonra diğer tüm sınıflar benzer bir kod içinde kullanılabilir. Aşağıdaki kod örneğinde yeni bir örneğini döndürür `rssChannelImage` sınıfı.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
