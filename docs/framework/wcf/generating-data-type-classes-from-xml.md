---
title: "XML'den Veri Türü Sınıfları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0362673ebb7d686822fae594b3a41435ceb9a4d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="86c2b-102">XML'den Veri Türü Sınıfları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86c2b-102">Generating Data Type Classes from XML</span></span>
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<span data-ttu-id="86c2b-103">XML'den veri türü sınıfları oluşturmak için yeni bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="86c2b-103"> includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="86c2b-104">Bu konu, veri türleri .NET Blog RSS akışı için otomatik olarak oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="86c2b-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="86c2b-105">.NET Blog RSS XML alma akış</span><span class="sxs-lookup"><span data-stu-id="86c2b-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1.  <span data-ttu-id="86c2b-106">Internet Explorer'a gidin [.NET Blog RSS akışı](https://blogs.msdn.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="86c2b-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://blogs.msdn.microsoft.com/dotnet/feed/).</span></span>  
  
2.  <span data-ttu-id="86c2b-107">Sayfanın sağ tıklatıp **kaynağı görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="86c2b-107">Right-click the page and select **View Source**.</span></span>  
  
3.  <span data-ttu-id="86c2b-108">Akışın metni tuşlarına basarak kopyalayın **Ctrl + A** tüm metni seçmek için ve **Ctrl + C** kopyalamak için.</span><span class="sxs-lookup"><span data-stu-id="86c2b-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="86c2b-109">Veri türleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="86c2b-109">Creating the data types</span></span>  
  
1.  <span data-ttu-id="86c2b-110">Kullanılacak proxy olduğu bir kod dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="86c2b-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="86c2b-111">Bu dosya parçası olması gereken bir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="86c2b-111">This file should be part of a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="86c2b-112">İmleci dosyası var olan tüm sınıflar dışında bir konuma yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="86c2b-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3.  <span data-ttu-id="86c2b-113">Seçin **Düzenle**, **Özel Yapıştır**, **XML sınıflar Yapıştır**.</span><span class="sxs-lookup"><span data-stu-id="86c2b-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4.  <span data-ttu-id="86c2b-114">Adlı sınıf `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` ve `rssChannelItemGuid` RSS akışı öğelerinde erişmek için gerekli üyelerle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86c2b-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="86c2b-115">Oluşturulan sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="86c2b-115">Using the generated classes</span></span>  
  
1.  <span data-ttu-id="86c2b-116">Sınıflar sonra diğer sınıflar gibi kodda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="86c2b-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="86c2b-117">Aşağıdaki kod örneğinde yeni bir örneğini döndürür `rssChannelImage` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="86c2b-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
