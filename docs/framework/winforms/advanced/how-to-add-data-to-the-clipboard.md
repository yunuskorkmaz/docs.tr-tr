---
title: "Nasıl yapılır: Panoya Veri Ekleme"
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
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47858af6d4e3dc5f29632c5a74f2431a2cc200b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="70ca1-102">Nasıl yapılır: Panoya Veri Ekleme</span><span class="sxs-lookup"><span data-stu-id="70ca1-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="70ca1-103"><xref:System.Windows.Forms.Clipboard> Sınıfı Windows işletim sistemi Pano özelliği ile etkileşim kurmak için kullanabileceğiniz yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="70ca1-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="70ca1-104">Birçok uygulama Pano verileri için geçici depo olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="70ca1-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="70ca1-105">Örneğin, sözcük işlemci kesme ve yapıştırma işlemleri sırasında Panosu'nu kullanın.</span><span class="sxs-lookup"><span data-stu-id="70ca1-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="70ca1-106">Pano, bir uygulamadan başka bir veri aktarmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="70ca1-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="70ca1-107">Panoya veri eklediğinizde, bu biçimi kullanıyorsanız diğer uygulamaların veri tanıyabilmesi veri biçimi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ca1-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="70ca1-108">Veri kullanabilmeniz için diğer uygulamaları sayısını artırmak için panoya birden çok farklı biçimlerde verileri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ca1-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="70ca1-109">Böylece bu biçimi kullanan bir uygulamayı ilişkili veri biçimini tanımlayan bir dize bir Pano biçimidir.</span><span class="sxs-lookup"><span data-stu-id="70ca1-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="70ca1-110"><xref:System.Windows.Forms.DataFormats> Sınıfı kullanmanız için önceden tanımlanmış biçim adlarının sağlar.</span><span class="sxs-lookup"><span data-stu-id="70ca1-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="70ca1-111">Ayrıca, kendi biçim adları kullanın veya bir nesne türünü, biçimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ca1-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="70ca1-112">Bir veya birden çok biçimlerde Pano veri eklemek için kullanın <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="70ca1-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="70ca1-113">Bu yöntem herhangi bir nesne geçirebilirsiniz ancak çoklu biçimlerde veri eklemek için önce verileri birden çok biçim ile çalışmak üzere tasarlanmış ayrı bir nesne eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="70ca1-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="70ca1-114">Genellikle, verilerinizi ekleyecek bir <xref:System.Windows.Forms.DataObject>, ancak uygulayan herhangi bir türü kullanabilirsiniz <xref:System.Windows.Forms.IDataObject> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="70ca1-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="70ca1-115">İçinde [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], temel Pano görevleri kolaylaştırmak için tasarlanmış yeni yöntemlerle doğrudan panoya verileri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70ca1-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="70ca1-116">Metin gibi tek, ortak biçiminde verilerle çalışırken bu yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="70ca1-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70ca1-117">Tüm Windows tabanlı uygulamalar Pano paylaşır.</span><span class="sxs-lookup"><span data-stu-id="70ca1-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="70ca1-118">Bu nedenle, başka bir uygulamaya geçiş yaptığınızda içeriği değiştirilebilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="70ca1-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="70ca1-119"><xref:System.Windows.Forms.Clipboard> Sınıfı yalnızca kullanılabilir iş parçacıklarında tek iş parçacığı Grup (STA) modu olarak ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="70ca1-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="70ca1-120">Bu sınıf kullanmak için emin olun, `Main` yöntemi ile işaretlenmiş <xref:System.STAThreadAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70ca1-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="70ca1-121">Bir nesne Pano'ya yerleştir kendisine için Serileştirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70ca1-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="70ca1-122">Türü seri hale getirilebilir yapmak için kendisiyle işaretlemek <xref:System.SerializableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70ca1-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="70ca1-123">Bir Pano yönteme serileştirilebilir olmayan bir nesne geçirirseniz, yöntem bir özel durum atma olmadan başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="70ca1-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="70ca1-124">Seri hale getirme hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="70ca1-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="70ca1-125">Tek, ortak bir biçimde Pano veri eklemek için</span><span class="sxs-lookup"><span data-stu-id="70ca1-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="70ca1-126">Kullanım <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, veya <xref:System.Windows.Forms.Clipboard.SetText%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="70ca1-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="70ca1-127">Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70ca1-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="70ca1-128">Özel bir biçim panoya veri eklemek için</span><span class="sxs-lookup"><span data-stu-id="70ca1-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="70ca1-129">Kullanım <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi bir özel biçim adına sahip.</span><span class="sxs-lookup"><span data-stu-id="70ca1-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="70ca1-130">Bu yöntem yalnızca kullanılabilir [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70ca1-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="70ca1-131">Önceden tanımlanmış biçim adıyla de kullanabilirsiniz <xref:System.Windows.Forms.Clipboard.SetData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="70ca1-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="70ca1-132">Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="70ca1-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="70ca1-133">Birden çok biçim panoya veri eklemek için</span><span class="sxs-lookup"><span data-stu-id="70ca1-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="70ca1-134">Kullanım <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> yöntemi ve geçişinde bir <xref:System.Windows.Forms.DataObject> verilerinizi içeren.</span><span class="sxs-lookup"><span data-stu-id="70ca1-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="70ca1-135">Sürümleri panoya veri eklemek için bu yöntemi kullanın öncesi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70ca1-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="70ca1-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70ca1-136">See Also</span></span>  
 [<span data-ttu-id="70ca1-137">Sürükle ve bırak işlemleri ve Pano desteği</span><span class="sxs-lookup"><span data-stu-id="70ca1-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="70ca1-138">Nasıl yapılır: panodan veri alma</span><span class="sxs-lookup"><span data-stu-id="70ca1-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
