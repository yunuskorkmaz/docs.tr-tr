---
title: XML'den Veri Türü Sınıfları Oluşturma
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: a7920a8c8c4f279dd3fc52029c5da5e9b685efe2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238255"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="fcec4-102">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcec4-102">Generating Data Type Classes from XML</span></span>

<span data-ttu-id="fcec4-103">.NET Framework 4,5, XML 'den veri türü sınıfları oluşturmak için yeni bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="fcec4-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="fcec4-104">Bu konu başlığında, .NET blog RSS akışı için otomatik olarak veri türleri oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fcec4-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="fcec4-105">.NET blog RSS akışından XML edinme</span><span class="sxs-lookup"><span data-stu-id="fcec4-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="fcec4-106">Internet Explorer 'da [.net blog RSS akışına](https://devblogs.microsoft.com/dotnet/feed/)gidin.</span><span class="sxs-lookup"><span data-stu-id="fcec4-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="fcec4-107">Sayfaya sağ tıklayın ve **kaynağı görüntüle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="fcec4-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="fcec4-108">Tüm metni seçmek için **CTRL + A** tuşlarına basarak akışın metnini kopyalayın ve kopyalamak için **CTRL + C** ' ye basın.</span><span class="sxs-lookup"><span data-stu-id="fcec4-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="fcec4-109">Veri türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="fcec4-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="fcec4-110">Proxy 'nin kullanılacağı bir kod dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="fcec4-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="fcec4-111">Bu dosya .NET Framework 4,5 projesinin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fcec4-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="fcec4-112">İmleci dosyadaki bir konuma var olan sınıfların dışında yerleştir.</span><span class="sxs-lookup"><span data-stu-id="fcec4-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="fcec4-113">**Düzenle**, **Özel Yapıştır**, **XML 'i sınıflar olarak Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="fcec4-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="fcec4-114">,,, Ve adlı sınıflar `link` , `rss` `rssChannel` `rssChannelImage` `rssChannelItem` `rssChannelItemGuid` RSS akışındaki öğelere erişmek için gerekli üyelerle birlikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fcec4-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="fcec4-115">Oluşturulan sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="fcec4-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="fcec4-116">Sınıflar oluşturulduktan sonra, diğer sınıflar gibi kodda kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="fcec4-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="fcec4-117">Aşağıdaki kod örneği, sınıfının yeni bir örneğini döndürür `rssChannelImage` .</span><span class="sxs-lookup"><span data-stu-id="fcec4-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
