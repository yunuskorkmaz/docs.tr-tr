---
title: 'Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 0a9dcd00d4bc3e64ae4fc9a1d4884fac18521825
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181226"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="2062a-102">Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2062a-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2062a-103">yazı tipleri ile aynı yazı tipi ancak farklı stillerde yazı tipi aileleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="2062a-103">groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="2062a-104">Örneğin, aşağıdaki yazı tipleri Arial yazı tipi ailesini içerir:</span><span class="sxs-lookup"><span data-stu-id="2062a-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="2062a-105">Arial normal</span><span class="sxs-lookup"><span data-stu-id="2062a-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="2062a-106">Arial kalın</span><span class="sxs-lookup"><span data-stu-id="2062a-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="2062a-107">Arial İtalik</span><span class="sxs-lookup"><span data-stu-id="2062a-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="2062a-108">Arial Kalın İtalik</span><span class="sxs-lookup"><span data-stu-id="2062a-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2062a-109">form aileleri için dört stilleri kullanır: normal, kalın, italik ve kalın italik.</span><span class="sxs-lookup"><span data-stu-id="2062a-109">uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="2062a-110">Sıfat gibi *daraltmak* ve *yuvarlatılmış* stilleri; dikkate alınmaz aile adı bir parçası olduklarından değil.</span><span class="sxs-lookup"><span data-stu-id="2062a-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="2062a-111">Örneğin, dar Arial yazı tipi ailesi aşağıdaki üyeleri ile şöyledir:</span><span class="sxs-lookup"><span data-stu-id="2062a-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="2062a-112">Arial dar normal</span><span class="sxs-lookup"><span data-stu-id="2062a-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="2062a-113">Arial dar kalın</span><span class="sxs-lookup"><span data-stu-id="2062a-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="2062a-114">Arial dar italik</span><span class="sxs-lookup"><span data-stu-id="2062a-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="2062a-115">Dar Arial Kalın İtalik</span><span class="sxs-lookup"><span data-stu-id="2062a-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="2062a-116">Metinle çizebilirsiniz önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.FontFamily> nesnesi ve bir <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="2062a-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="2062a-117"><xref:System.Drawing.FontFamily> Nesnesini belirtir (örneğin, Arial), yazı tipi ve <xref:System.Drawing.Font> boyutu, stil ve birimler nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2062a-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2062a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="2062a-118">Example</span></span>  
 <span data-ttu-id="2062a-119">Aşağıdaki örnek, bir Normal stili Arial yazı tipi boyutu 16 piksel olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2062a-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="2062a-120">Aşağıdaki kodda, ilk bağımsız değişkenin geçirilecek <xref:System.Drawing.Font.%23ctor%2A> oluşturucudur <xref:System.Drawing.FontFamily> nesne.</span><span class="sxs-lookup"><span data-stu-id="2062a-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="2062a-121">İkinci bağımsız değişkeni Dördüncü bağımsız değişkeni tarafından tanımlanan birimleri cinsinden ölçülen yazı tipi boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2062a-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="2062a-122">Üçüncü bağımsız değişken stil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2062a-122">The third argument identifies the style.</span></span>  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> <span data-ttu-id="2062a-123">bir üyesidir <xref:System.Drawing.GraphicsUnit> numaralandırma ve <xref:System.Drawing.FontStyle.Regular> üyesi <xref:System.Drawing.FontStyle> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2062a-123">is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2062a-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2062a-124">Compiling the Code</span></span>  
 <span data-ttu-id="2062a-125">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs>`e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="2062a-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2062a-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2062a-126">See also</span></span>

- [<span data-ttu-id="2062a-127">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="2062a-127">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="2062a-128">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="2062a-128">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
