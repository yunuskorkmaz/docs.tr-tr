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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="83db9-102">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="83db9-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="83db9-103">.NET framework 4.5, XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="83db9-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="83db9-104">Bu konuda, veri türleri .NET blogu RSS akışı için otomatik olarak oluşturacak şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="83db9-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="83db9-105">XML alma .NET blogu RSS akışı</span><span class="sxs-lookup"><span data-stu-id="83db9-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="83db9-106">Internet Explorer'da gidin [.NET blogu RSS akışı](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="83db9-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="83db9-107">Sayfanın sağ tıklayıp **kaynağı görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="83db9-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="83db9-108">Akışın metni tuşlarına basarak kopyalayın **Ctrl + A** tüm metni seçmek için ve **Ctrl + C** kopyalanacak.</span><span class="sxs-lookup"><span data-stu-id="83db9-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="83db9-109">Veri türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="83db9-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="83db9-110">Kullanılacak proxy olduğu bir kod dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="83db9-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="83db9-111">Bu dosya, .NET Framework 4.5 projesinin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83db9-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="83db9-112">Dosyanın mevcut tüm sınıflar dışında bir konumda imleci yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="83db9-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="83db9-113">Seçin **Düzenle**, **Özel Yapıştır**, **XML sınıflar Yapıştır**.</span><span class="sxs-lookup"><span data-stu-id="83db9-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="83db9-114">Sınıflar adlandırılan `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` ve `rssChannelItemGuid` RSS akışı öğeleri erişmek için gereken üyeleri ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="83db9-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="83db9-115">Oluşturulan sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="83db9-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="83db9-116">Sınıfları oluşturduktan sonra diğer tüm sınıflar benzer bir kod içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="83db9-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="83db9-117">Aşağıdaki kod örneğinde yeni bir örneğini döndürür `rssChannelImage` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="83db9-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
