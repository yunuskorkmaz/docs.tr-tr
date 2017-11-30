---
title: "Nasıl yapılır: Panodan Veri Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2f71c6738f19e70826b95626377097de0cd9b3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a><span data-ttu-id="cc7a0-102">Nasıl yapılır: Panodan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="cc7a0-102">How to: Retrieve Data from the Clipboard</span></span>
<span data-ttu-id="cc7a0-103"><xref:System.Windows.Forms.Clipboard> Sınıfı Windows işletim sistemi Pano özelliği ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="cc7a0-104">Birçok uygulama Pano verileri için geçici depo olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="cc7a0-105">Örneğin, sözcük işlemci kesme ve yapıştırma işlemleri sırasında Panosu'nu kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="cc7a0-106">Pano, bir uygulamadan diğerine bilgileri aktarmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-106">The Clipboard is also useful for transferring information from one application to another.</span></span>  
  
 <span data-ttu-id="cc7a0-107">Bazı uygulamalar, veriler kullanabilmeniz için diğer uygulamaları sayısını artırmak için Pano'ya çoklu biçimlerde verileri depolar.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-107">Some applications store data on the Clipboard in multiple formats to increase the number of other applications that can potentially use the data.</span></span> <span data-ttu-id="cc7a0-108">Pano biçimi biçimini tanımlayan bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-108">A Clipboard format is a string that identifies the format.</span></span> <span data-ttu-id="cc7a0-109">Tanımlanan biçimi kullanan bir uygulamayı Pano'daki ilişkili veri alabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-109">An application that uses the identified format can retrieve the associated data on the Clipboard.</span></span> <span data-ttu-id="cc7a0-110"><xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adlarının sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="cc7a0-111">Ayrıca, kendi biçim adları kullanın veya bir nesnenin türünü, biçimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-111">You can also use your own format names or use an object's type as its format.</span></span> <span data-ttu-id="cc7a0-112">Panoya veri ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: panoya veri ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).</span><span class="sxs-lookup"><span data-stu-id="cc7a0-112">For information about adding data to the Clipboard, see [How to: Add Data to the Clipboard](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).</span></span>  
  
 <span data-ttu-id="cc7a0-113">Pano belirli bir biçimde veri içerip içermediğini belirlemek için aşağıdakilerden birini kullanmak `Contains` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-113">To determine whether the Clipboard contains data in a particular format, use one of the `Contains`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="cc7a0-114">Pano verilerini almak için aşağıdakilerden birini kullanın `Get` *biçimi* yöntemleri veya <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-114">To retrieve data from the Clipboard, use one of the `Get`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="cc7a0-115">Bu yöntemler yeni [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc7a0-115">These methods are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
 <span data-ttu-id="cc7a0-116">Sürümleri kullanarak panodan verilere erişme öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], kullanın <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi ve dönen yöntemlerini çağıran <xref:System.Windows.Forms.IDataObject>.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-116">To access data from the Clipboard by using versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method and call the methods of the returned <xref:System.Windows.Forms.IDataObject>.</span></span> <span data-ttu-id="cc7a0-117">Örneğin, belirli bir biçimde nesnesine döndürülen kullanılabilir olup olmadığını belirlemek için arama <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-117">To determine whether a particular format is available in the returned object, for example, call the <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc7a0-118">Tüm Windows tabanlı uygulamalar Pano sistem paylaşır.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-118">All Windows-based applications share the system Clipboard.</span></span> <span data-ttu-id="cc7a0-119">Bu nedenle, başka bir uygulamaya geçiş yaptığınızda içeriği değiştirilebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-119">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="cc7a0-120"><xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) modu olarak ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-120">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="cc7a0-121">Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-121">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="cc7a0-122">Tek, ortak bir biçimde panodan veri almak için</span><span class="sxs-lookup"><span data-stu-id="cc7a0-122">To retrieve data from the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="cc7a0-123">Kullanım <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.GetText%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-123">Use the <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, or <xref:System.Windows.Forms.Clipboard.GetText%2A> method.</span></span> <span data-ttu-id="cc7a0-124">İsteğe bağlı olarak, karşılık gelen kullanmak `Contains` *biçimi* ilk veri belirli bir biçimde kullanılabilir olup olmadığını belirlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-124">Optionally, use the corresponding `Contains`*Format* methods first to determine whether data is available in a particular format.</span></span> <span data-ttu-id="cc7a0-125">Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc7a0-125">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a><span data-ttu-id="cc7a0-126">Özel bir biçim panoya veri almak için</span><span class="sxs-lookup"><span data-stu-id="cc7a0-126">To retrieve data from the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="cc7a0-127">Kullanım <xref:System.Windows.Forms.Clipboard.GetData%2A> yöntemi bir özel biçim adına sahip.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-127">Use the <xref:System.Windows.Forms.Clipboard.GetData%2A> method with a custom format name.</span></span> <span data-ttu-id="cc7a0-128">Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc7a0-128">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="cc7a0-129">Önceden tanımlanmış biçim adıyla de kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-129">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="cc7a0-130">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-130">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a><span data-ttu-id="cc7a0-131">Çoklu biçimlerde panodan veri almak için</span><span class="sxs-lookup"><span data-stu-id="cc7a0-131">To retrieve data from the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="cc7a0-132">Kullanım <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-132">Use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method.</span></span> <span data-ttu-id="cc7a0-133">Sürümlerinde panodan veri almak için bu yöntemi kullanın öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc7a0-133">You must use this method to retrieve data from the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="cc7a0-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc7a0-134">See Also</span></span>  
 [<span data-ttu-id="cc7a0-135">Sürükle ve bırak işlemleri ve Pano desteği</span><span class="sxs-lookup"><span data-stu-id="cc7a0-135">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="cc7a0-136">Nasıl yapılır: panoya veri ekleme</span><span class="sxs-lookup"><span data-stu-id="cc7a0-136">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
