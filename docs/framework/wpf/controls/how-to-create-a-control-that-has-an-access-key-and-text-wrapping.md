---
title: 'Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 8343c660ddeb5487f46e87534e555936d1b86371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553799"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="f427e-102">Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f427e-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="f427e-103">Bu örnek, bir erişim anahtarı olan ve metin kaydırma destekleyen bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f427e-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="f427e-104">Örnek kullanan bir <xref:System.Windows.Controls.Label> bu kavramları göstermek için denetim.</span><span class="sxs-lookup"><span data-stu-id="f427e-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f427e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f427e-105">Example</span></span>  
 <span data-ttu-id="f427e-106">**Metin kaydırma için etiket ekleme**</span><span class="sxs-lookup"><span data-stu-id="f427e-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="f427e-107"><xref:System.Windows.Controls.Label> Denetimi metin kaydırma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f427e-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="f427e-108">Birden çok satıra yayılmış saran bir etiket gerekirse, sarmalama ve öğe etiketi içinde put metin desteklemiyor başka bir öğe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f427e-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="f427e-109">Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.TextBlock> birkaç satırlık metin saran bir etiket yapmak için.</span><span class="sxs-lookup"><span data-stu-id="f427e-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="f427e-110">**Erişim anahtarı ve metin kaydırma için etiket ekleme**</span><span class="sxs-lookup"><span data-stu-id="f427e-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="f427e-111">Gerekirse bir <xref:System.Windows.Controls.Label> bir erişim anahtarı (anımsatıcı) olan, kullanın <xref:System.Windows.Controls.AccessText> içinde olan öğeyi <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="f427e-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="f427e-112">Gibi denetimler <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, ve <xref:System.Windows.Controls.GroupBox> varsayılan denetim şablonlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f427e-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="f427e-113">Bu şablonlarını içeren bir <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="f427e-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="f427e-114">Üzerinde ayarlayabileceğiniz özelliklerden birini <xref:System.Windows.Controls.ContentPresenter> olan <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", bu denetim için erişim anahtarı belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f427e-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="f427e-115">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Label> , bir erişim anahtarı olan ve metin kaydırma destekler.</span><span class="sxs-lookup"><span data-stu-id="f427e-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="f427e-116">Metin kaydırma, örnek kümeleri etkinleştirmek için <xref:System.Windows.Controls.AccessText.TextWrapping%2A> özelliği ve kullandığı altı çizili karakter erişim tuşu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f427e-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="f427e-117">(Alt çizgi karakteri hemen izleyen karakterin erişim anahtardır.)</span><span class="sxs-lookup"><span data-stu-id="f427e-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f427e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f427e-118">See Also</span></span>  
 [<span data-ttu-id="f427e-119">Nasıl yapılır: bir etiket için Target özelliği ayarlama</span><span class="sxs-lookup"><span data-stu-id="f427e-119">How to: Set the Target Property of a Label</span></span>](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
