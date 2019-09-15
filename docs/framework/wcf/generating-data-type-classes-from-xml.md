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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="f43b9-102">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f43b9-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="f43b9-103">.NET Framework 4,5, XML 'den veri türü sınıfları oluşturmak için yeni bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="f43b9-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="f43b9-104">Bu konu başlığında, .NET blog RSS akışı için otomatik olarak veri türleri oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f43b9-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="f43b9-105">.NET blog RSS akışından XML edinme</span><span class="sxs-lookup"><span data-stu-id="f43b9-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="f43b9-106">Internet Explorer 'da [.net blog RSS akışına](https://devblogs.microsoft.com/dotnet/feed/)gidin.</span><span class="sxs-lookup"><span data-stu-id="f43b9-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="f43b9-107">Sayfaya sağ tıklayın ve **kaynağı görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f43b9-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="f43b9-108">Tüm metni seçmek için **CTRL + A** tuşlarına basarak akışın metnini kopyalayın ve kopyalamak için **CTRL + C** ' ye basın.</span><span class="sxs-lookup"><span data-stu-id="f43b9-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="f43b9-109">Veri türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="f43b9-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="f43b9-110">Proxy 'nin kullanılacağı bir kod dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="f43b9-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="f43b9-111">Bu dosya .NET Framework 4,5 projesinin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f43b9-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="f43b9-112">İmleci dosyadaki bir konuma var olan sınıfların dışında yerleştir.</span><span class="sxs-lookup"><span data-stu-id="f43b9-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="f43b9-113">**Düzenle**, **Özel Yapıştır**, **XML 'i sınıflar olarak Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f43b9-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="f43b9-114">,, `link`, `rss` `rssChannel` `rssChannelImage`Ve adlı`rssChannelItemGuid` sınıflar, RSS akışındaki öğelere erişmek için gerekli üyelerle birlikte oluşturulur. `rssChannelItem`</span><span class="sxs-lookup"><span data-stu-id="f43b9-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="f43b9-115">Oluşturulan sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="f43b9-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="f43b9-116">Sınıflar oluşturulduktan sonra, diğer sınıflar gibi kodda kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="f43b9-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="f43b9-117">Aşağıdaki kod örneği, `rssChannelImage` sınıfının yeni bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f43b9-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
