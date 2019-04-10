---
title: XML'den Veri Türü Sınıfları Oluşturma
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: c1b5dfda8aa5370dbc202ab90c75ab5677970467
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309348"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="96abe-102">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96abe-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] <span data-ttu-id="96abe-103">XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="96abe-103">includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="96abe-104">Bu konuda, veri türleri .NET blogu RSS akışı için otomatik olarak oluşturacak şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="96abe-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="96abe-105">XML alma .NET blogu RSS akışı</span><span class="sxs-lookup"><span data-stu-id="96abe-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="96abe-106">Internet Explorer'da gidin [.NET blogu RSS akışı](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="96abe-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="96abe-107">Sayfanın sağ tıklayıp **kaynağı görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="96abe-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="96abe-108">Akışın metni tuşlarına basarak kopyalayın **Ctrl + A** tüm metni seçmek için ve **Ctrl + C** kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="96abe-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="96abe-109">Veri türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="96abe-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="96abe-110">Kullanılacak proxy olduğu bir kod dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="96abe-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="96abe-111">Bu dosya parçası olması gereken bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] proje.</span><span class="sxs-lookup"><span data-stu-id="96abe-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2. <span data-ttu-id="96abe-112">Dosyanın mevcut tüm sınıflar dışında bir konumda imleci yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="96abe-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="96abe-113">Seçin **Düzenle**, **Özel Yapıştır**, **XML sınıflar Yapıştır**.</span><span class="sxs-lookup"><span data-stu-id="96abe-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="96abe-114">Sınıflar adlandırılan `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` ve `rssChannelItemGuid` RSS akışı öğeleri erişmek için gereken üyeleri ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="96abe-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="96abe-115">Oluşturulan sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="96abe-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="96abe-116">Sınıfları oluşturduktan sonra diğer tüm sınıflar benzer bir kod içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96abe-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="96abe-117">Aşağıdaki kod örneğinde yeni bir örneğini döndürür `rssChannelImage` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="96abe-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
