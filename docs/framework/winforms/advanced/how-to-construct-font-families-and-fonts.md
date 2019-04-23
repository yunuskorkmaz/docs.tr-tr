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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181226"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="1ec00-102">Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ec00-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="1ec00-103">yazı tipleri ile aynı yazı tipi ancak farklı stillerde yazı tipi aileleri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="1ec00-103">groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="1ec00-104">Örneğin, aşağıdaki yazı tipleri Arial yazı tipi ailesini içerir:</span><span class="sxs-lookup"><span data-stu-id="1ec00-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="1ec00-105">Arial normal</span><span class="sxs-lookup"><span data-stu-id="1ec00-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="1ec00-106">Arial kalın</span><span class="sxs-lookup"><span data-stu-id="1ec00-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="1ec00-107">Arial İtalik</span><span class="sxs-lookup"><span data-stu-id="1ec00-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="1ec00-108">Arial Kalın İtalik</span><span class="sxs-lookup"><span data-stu-id="1ec00-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="1ec00-109">form aileleri için dört stilleri kullanır: normal, kalın, italik ve kalın italik.</span><span class="sxs-lookup"><span data-stu-id="1ec00-109">uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="1ec00-110">Sıfat gibi *daraltmak* ve *yuvarlatılmış* stilleri; dikkate alınmaz aile adı bir parçası olduklarından değil.</span><span class="sxs-lookup"><span data-stu-id="1ec00-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="1ec00-111">Örneğin, dar Arial yazı tipi ailesi aşağıdaki üyeleri ile şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1ec00-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="1ec00-112">Arial dar normal</span><span class="sxs-lookup"><span data-stu-id="1ec00-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="1ec00-113">Arial dar kalın</span><span class="sxs-lookup"><span data-stu-id="1ec00-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="1ec00-114">Arial dar italik</span><span class="sxs-lookup"><span data-stu-id="1ec00-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="1ec00-115">Dar Arial Kalın İtalik</span><span class="sxs-lookup"><span data-stu-id="1ec00-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="1ec00-116">Metinle çizebilirsiniz önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.FontFamily> nesnesi ve bir <xref:System.Drawing.Font> nesne.</span><span class="sxs-lookup"><span data-stu-id="1ec00-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="1ec00-117"><xref:System.Drawing.FontFamily> Nesnesini belirtir (örneğin, Arial), yazı tipi ve <xref:System.Drawing.Font> boyutu, stil ve birimler nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ec00-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ec00-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ec00-118">Example</span></span>  
 <span data-ttu-id="1ec00-119">Aşağıdaki örnek, bir Normal stili Arial yazı tipi boyutu 16 piksel olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1ec00-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="1ec00-120">Aşağıdaki kodda, ilk bağımsız değişkenin geçirilecek <xref:System.Drawing.Font.%23ctor%2A> oluşturucudur <xref:System.Drawing.FontFamily> nesne.</span><span class="sxs-lookup"><span data-stu-id="1ec00-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="1ec00-121">İkinci bağımsız değişkeni Dördüncü bağımsız değişkeni tarafından tanımlanan birimleri cinsinden ölçülen yazı tipi boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ec00-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="1ec00-122">Üçüncü bağımsız değişken stil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1ec00-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="1ec00-123"><xref:System.Drawing.GraphicsUnit.Pixel> bir üyesidir <xref:System.Drawing.GraphicsUnit> numaralandırma ve <xref:System.Drawing.FontStyle.Regular> üyesi <xref:System.Drawing.FontStyle> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1ec00-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1ec00-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1ec00-124">Compiling the Code</span></span>  
 <span data-ttu-id="1ec00-125">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1ec00-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec00-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ec00-126">See also</span></span>

- [<span data-ttu-id="1ec00-127">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="1ec00-127">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="1ec00-128">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="1ec00-128">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
