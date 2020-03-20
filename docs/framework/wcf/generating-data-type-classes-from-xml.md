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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="66391-102">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="66391-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="66391-103">.NET Framework 4.5, XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="66391-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="66391-104">Bu konu, .NET Blog RSS akışı için veri türlerinin otomatik olarak nasıl üretilebildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="66391-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="66391-105">.NET Blog RSS akışından XML alma</span><span class="sxs-lookup"><span data-stu-id="66391-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="66391-106">Internet Explorer'da [,.NET Blog RSS akışına](https://devblogs.microsoft.com/dotnet/feed/)gidin.</span><span class="sxs-lookup"><span data-stu-id="66391-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="66391-107">Sayfaya sağ tıklayın ve **Kaynağı Görüntüle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="66391-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="66391-108">Tüm metni seçmek için **Ctrl+A** tuşuna basarak özet akışının metnini ve kopyalamak için **Ctrl+C'yi** kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="66391-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="66391-109">Veri türlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="66391-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="66391-110">Proxy'nin kullanılacağı bir kod dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="66391-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="66391-111">Bu dosya bir .NET Framework 4.5 projesinin bir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66391-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="66391-112">İmleci dosyadaki bir konuma varolan sınıfların dışına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="66391-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="66391-113">Sınıf olarak **Yap,** **Yapıştır Özel**, **Yapıştır XML'i seçin.**</span><span class="sxs-lookup"><span data-stu-id="66391-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="66391-114">, `link`, `rss` `rssChannel`, `rssChannelImage` `rssChannelItem` , `rssChannelItemGuid` adlı sınıflar ve RSS akışındaki öğelere erişmek için gerekli üyelerle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66391-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="66391-115">Oluşturulan sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="66391-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="66391-116">Sınıflar oluşturulduktan sonra, diğer sınıflar gibi kod olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66391-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="66391-117">Aşağıdaki kod örneği sınıfın yeni `rssChannelImage` bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="66391-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
