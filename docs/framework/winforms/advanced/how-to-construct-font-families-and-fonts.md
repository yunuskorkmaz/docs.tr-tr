---
title: "Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma"
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
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 066cf358e43dabb3b952b32ecec34ca77c6e8c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="572ae-102">Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="572ae-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="572ae-103">yazı tipleri aynı yazı tipi ancak farklı stillerde yazı tipi aileleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="572ae-103"> groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="572ae-104">Örneğin, aşağıdaki yazı tipleri Arial yazı tipi ailesinin içerir:</span><span class="sxs-lookup"><span data-stu-id="572ae-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="572ae-105">Arial normal</span><span class="sxs-lookup"><span data-stu-id="572ae-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="572ae-106">Arial kalın</span><span class="sxs-lookup"><span data-stu-id="572ae-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="572ae-107">Arial İtalik</span><span class="sxs-lookup"><span data-stu-id="572ae-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="572ae-108">Arial Kalın İtalik</span><span class="sxs-lookup"><span data-stu-id="572ae-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="572ae-109">form aileleri için dört stillerini kullanır: normal, kalın, italik ve kalın italik.</span><span class="sxs-lookup"><span data-stu-id="572ae-109"> uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="572ae-110">Sıfatları gibi *daraltmak* ve *yuvarlanmasını* stilleri; dikkate alınmaz yerine bunların, aile adı bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="572ae-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="572ae-111">Örneğin, Arial dar bir yazı tipi ailesi aşağıdaki üyeleri ile şöyledir:</span><span class="sxs-lookup"><span data-stu-id="572ae-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="572ae-112">Arial dar normal</span><span class="sxs-lookup"><span data-stu-id="572ae-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="572ae-113">Arial Narrow Kalın</span><span class="sxs-lookup"><span data-stu-id="572ae-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="572ae-114">Arial Narrow İtalik</span><span class="sxs-lookup"><span data-stu-id="572ae-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="572ae-115">Arial Narrow Kalın İtalik</span><span class="sxs-lookup"><span data-stu-id="572ae-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="572ae-116">Metinle çizmeden önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.FontFamily> nesne ve <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="572ae-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="572ae-117"><xref:System.Drawing.FontFamily> Nesnesini belirtir (örneğin, Arial), yazı tipi ve <xref:System.Drawing.Font> nesnesini belirtir. boyutu, stil ve birimler.</span><span class="sxs-lookup"><span data-stu-id="572ae-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="572ae-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="572ae-118">Example</span></span>  
 <span data-ttu-id="572ae-119">Aşağıdaki örnek, Normal stili Arial yazı tipi boyutu 16 piksel olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="572ae-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="572ae-120">Aşağıdaki kodda için ilk bağımsız değişken geçirildi <xref:System.Drawing.Font.%23ctor%2A> Oluşturucusu olan <xref:System.Drawing.FontFamily> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="572ae-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="572ae-121">İkinci bağımsız değişken dördüncü bağımsız değişkeni tarafından tanımlanan birimler cinsinden yazı tipi boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="572ae-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="572ae-122">Üçüncü bağımsız değişken stilini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="572ae-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="572ae-123"><xref:System.Drawing.GraphicsUnit.Pixel>üye <xref:System.Drawing.GraphicsUnit> numaralandırma, ve <xref:System.Drawing.FontStyle.Regular> üyesi <xref:System.Drawing.FontStyle> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="572ae-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="572ae-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="572ae-124">Compiling the Code</span></span>  
 <span data-ttu-id="572ae-125">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="572ae-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572ae-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="572ae-126">See Also</span></span>  
 [<span data-ttu-id="572ae-127">Yazı tipleri ve metin kullanma</span><span class="sxs-lookup"><span data-stu-id="572ae-127">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="572ae-128">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="572ae-128">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
