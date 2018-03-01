---
title: "Dönüştürme Sırası Neden Önemlidir"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order signficance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd3363a1afb8658ed3bb27359259cb752464507d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="why-transformation-order-is-significant"></a><span data-ttu-id="aae0d-102">Dönüştürme Sırası Neden Önemlidir</span><span class="sxs-lookup"><span data-stu-id="aae0d-102">Why Transformation Order Is Significant</span></span>
<span data-ttu-id="aae0d-103">Tek bir <xref:System.Drawing.Drawing2D.Matrix> nesnesi, tek bir dönüştürmeyi veya bir dizi dönüştürmeyi depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-103">A single <xref:System.Drawing.Drawing2D.Matrix> object can store a single transformation or a sequence of transformations.</span></span> <span data-ttu-id="aae0d-104">İkinci bileşik dönüştürme adı verilir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-104">The latter is called a composite transformation.</span></span> <span data-ttu-id="aae0d-105">Bileşik bir dönüştürme matrisi tek dönüştürmeler matrisleri çarpılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-105">The matrix of a composite transformation is obtained by multiplying the matrices of individual transformations.</span></span>  
  
## <a name="composite-transform-examples"></a><span data-ttu-id="aae0d-106">Bileşik dönüştürme örnekleri</span><span class="sxs-lookup"><span data-stu-id="aae0d-106">Composite Transform Examples</span></span>  
 <span data-ttu-id="aae0d-107">Bileşik bir dönüşümünde tek dönüştürmeler sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-107">In a composite transformation, the order of individual transformations is important.</span></span> <span data-ttu-id="aae0d-108">İlk döndürme, Ölçek, sonra Çevir, örneğin, farklı bir sonuç ilk Çevir, döndürme sonra ölçeği daha alırsınız.</span><span class="sxs-lookup"><span data-stu-id="aae0d-108">For example, if you first rotate, then scale, then translate, you get a different result than if you first translate, then rotate, then scale.</span></span> <span data-ttu-id="aae0d-109">İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bileşik dönüşümler soldan sağa yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-109">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], composite transformations are built from left to right.</span></span> <span data-ttu-id="aae0d-110">S, R ve T ölçek, döndürme ve çeviri matrisleri sırasıyla varsa, ürün SRT (sırayla) bu ilk ölçekler bileşik dönüştürme matrisini olduğundan, ardından döndürür, sonra çevirir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-110">If S, R, and T are scale, rotation, and translation matrices respectively, then the product SRT (in that order) is the matrix of the composite transformation that first scales, then rotates, then translates.</span></span> <span data-ttu-id="aae0d-111">Ürün tarafından üretilen matris SRT TRS ürün tarafından üretilen matris farklıdır.</span><span class="sxs-lookup"><span data-stu-id="aae0d-111">The matrix produced by the product SRT is different from the matrix produced by the product TRS.</span></span>  
  
 <span data-ttu-id="aae0d-112">Sırası önemlidir bir döndürme ve ölçekleme gibi dönüştürmeleri koordinat sistemi kaynağa göre yapılır nedenidir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-112">One reason order is significant is that transformations like rotation and scaling are done with respect to the origin of the coordinate system.</span></span> <span data-ttu-id="aae0d-113">Kaynağa ortalanmış bir nesneyi ölçekleme kaynağını çıktığınızda taşınan bir nesneyi ölçekleme daha farklı bir sonuç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aae0d-113">Scaling an object that is centered at the origin produces a different result than scaling an object that has been moved away from the origin.</span></span> <span data-ttu-id="aae0d-114">Benzer şekilde, kaynak ortalanmış bir nesne döndürme kaynağını çıktığınızda taşınmış olan bir nesne döndürme daha farklı bir sonuç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aae0d-114">Similarly, rotating an object that is centered at the origin produces a different result than rotating an object that has been moved away from the origin.</span></span>  
  
 <span data-ttu-id="aae0d-115">Aşağıdaki örnek, bileşik bir dönüşüm oluşturmak için ölçeklendirme, çevirme ve döndürme (sırayla) birleştirir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-115">The following example combines scaling, rotation and translation (in that order) to form a composite transformation.</span></span> <span data-ttu-id="aae0d-116">Bağımsız değişken <xref:System.Drawing.Drawing2D.MatrixOrder.Append> geçirilen <xref:System.Drawing.Graphics.RotateTransform%2A> yöntemi gösterir döndürme ölçeklendirme izler.</span><span class="sxs-lookup"><span data-stu-id="aae0d-116">The argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passed to the <xref:System.Drawing.Graphics.RotateTransform%2A> method indicates that the rotation will follow the scaling.</span></span> <span data-ttu-id="aae0d-117">Benzer şekilde, bağımsız değişkeni <xref:System.Drawing.Drawing2D.MatrixOrder.Append> geçirilen <xref:System.Drawing.Graphics.TranslateTransform%2A> yöntemi gösterir çeviri döndürme izler.</span><span class="sxs-lookup"><span data-stu-id="aae0d-117">Likewise, the argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> passed to the <xref:System.Drawing.Graphics.TranslateTransform%2A> method indicates that the translation will follow the rotation.</span></span> <span data-ttu-id="aae0d-118"><xref:System.Drawing.Drawing2D.MatrixOrder.Append>ve <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> üyeleri olan <xref:System.Drawing.Drawing2D.MatrixOrder> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="aae0d-118"><xref:System.Drawing.Drawing2D.MatrixOrder.Append> and <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> are members of the <xref:System.Drawing.Drawing2D.MatrixOrder> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 <span data-ttu-id="aae0d-119">Aşağıdaki örnek Yukarıdaki örnekteki gibi aynı yöntemi çağrısı yapar, ancak çağrıları sırasını tersine çevrildi.</span><span class="sxs-lookup"><span data-stu-id="aae0d-119">The following example makes the same method calls as the preceding example, but the order of the calls is reversed.</span></span> <span data-ttu-id="aae0d-120">Sonuçta elde edilen işlem sırası olan ilk Çevir, ilk ölçek daha çok farklı bir sonuç oluşturur, Ölçek sonra döndürme sonra döndürün, sonra çevir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-120">The resulting order of operations is first translate, then rotate, then scale, which produces a very different result than first scale, then rotate, then translate.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 <span data-ttu-id="aae0d-121">Bileşik dönüştürmeyi bireysel dönüşümler sırasını tersine çevirmek için bir yöntem çağrıları dizisini sırasını tersine çevirmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="aae0d-121">One way to reverse the order of individual transformations in a composite transformation is to reverse the order of a sequence of method calls.</span></span> <span data-ttu-id="aae0d-122">İşlemlerin sırasını denetlemek için ikinci bir yolu, matris order bağımsız değişkeni değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-122">A second way to control the order of operations is to change the matrix order argument.</span></span> <span data-ttu-id="aae0d-123">Aşağıdaki örnek bir önceki örnekte, hariç aynıdır <xref:System.Drawing.Drawing2D.MatrixOrder.Append> değiştirildi <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>.</span><span class="sxs-lookup"><span data-stu-id="aae0d-123">The following example is the same as the preceding example, except that <xref:System.Drawing.Drawing2D.MatrixOrder.Append> has been changed to <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>.</span></span> <span data-ttu-id="aae0d-124">Çevir, sırasıyla ve döndürün veya matris çarpım S, R ve T ölçek için matrislerini nerede SRT, sırayla yapılır.</span><span class="sxs-lookup"><span data-stu-id="aae0d-124">The matrix multiplication is done in the order SRT, where S, R, and T are the matrices for scale, rotate, and translate, respectively.</span></span> <span data-ttu-id="aae0d-125">Bileşik dönüştürme sırasını ilk ölçek döndürün, sonra çevir.</span><span class="sxs-lookup"><span data-stu-id="aae0d-125">The order of the composite transformation is first scale, then rotate, then translate.</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 <span data-ttu-id="aae0d-126">Hemen önceki örnek aynı sonucunda, bu konunun ilk örnekte sonucudur.</span><span class="sxs-lookup"><span data-stu-id="aae0d-126">The result of the immediately preceding example is the same as the result of the first example in this topic.</span></span> <span data-ttu-id="aae0d-127">Biz yöntem çağrılarını sırasını ve matris çarpım sırasını tersine olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="aae0d-127">This is because we reversed both the order of the method calls and the order of the matrix multiplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae0d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aae0d-128">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.Matrix>  
 [<span data-ttu-id="aae0d-129">Koordinat Sistemleri ve Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="aae0d-129">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="aae0d-130">Yönetilen GDI+'da Dönüştürmeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="aae0d-130">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
