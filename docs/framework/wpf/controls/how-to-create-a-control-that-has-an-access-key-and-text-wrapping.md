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
ms.openlocfilehash: 12410e2abd1031f7ac42bdaab4b8e09a6b8b6006
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649589"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a><span data-ttu-id="b0cbc-102">Nasıl yapılır: Erişim Anahtarı ve Metin Kaydırması İçeren bir Denetim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b0cbc-102">How to: Create a Control That Has an Access Key and Text Wrapping</span></span>
<span data-ttu-id="b0cbc-103">Bu örnek, bir erişim anahtarı ve metin kaydırma destekleyen bir denetim oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-103">This example shows how to create a control that has an access key and supports text wrapping.</span></span> <span data-ttu-id="b0cbc-104">Örnekte bir <xref:System.Windows.Controls.Label> bu kavramları göstermek için denetim.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-104">The example uses a <xref:System.Windows.Controls.Label> control to illustrate these concepts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0cbc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0cbc-105">Example</span></span>  
 <span data-ttu-id="b0cbc-106">**Metin kaydırmayı Etiketinize ekleyin**</span><span class="sxs-lookup"><span data-stu-id="b0cbc-106">**Add Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="b0cbc-107"><xref:System.Windows.Controls.Label> Denetim metin kaydırmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-107">The <xref:System.Windows.Controls.Label> control does not support text wrapping.</span></span> <span data-ttu-id="b0cbc-108">Birden çok satırda sarmalayan bir etiket gerekiyorsa, sarmalama ve öğe etiket içinde put metin destekleyen başka bir öğenin iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-108">If you need a label that wraps across multiple lines, you can nest another element that does support text wrapping and put the element inside the label.</span></span> <span data-ttu-id="b0cbc-109">Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.TextBlock> birkaç satırlık metin sarmalayan bir etiket yapma.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-109">The following example shows how to use a <xref:System.Windows.Controls.TextBlock> to make a label that wraps several lines of text.</span></span>  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 <span data-ttu-id="b0cbc-110">**Erişim anahtarı ve metin kaydırması Etiketinize ekleyin**</span><span class="sxs-lookup"><span data-stu-id="b0cbc-110">**Add an Access Key and Text Wrapping to Your Label**</span></span>  
  
 <span data-ttu-id="b0cbc-111">Gerekirse bir <xref:System.Windows.Controls.Label> kullanmak, bir erişim anahtarı (anımsatıcı) olan <xref:System.Windows.Controls.AccessText> içinde öğesi <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-111">If you need a <xref:System.Windows.Controls.Label> that has an access key (mnemonic), use the <xref:System.Windows.Controls.AccessText> element that is inside the <xref:System.Windows.Controls.Label>.</span></span>  
  
 <span data-ttu-id="b0cbc-112">Gibi denetimler <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, ve <xref:System.Windows.Controls.GroupBox> varsayılan denetim şablonları vardır.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-112">Controls such as <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, and <xref:System.Windows.Controls.GroupBox> have default control templates.</span></span> <span data-ttu-id="b0cbc-113">Bu şablonlar içeren bir <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-113">These templates contain a <xref:System.Windows.Controls.ContentPresenter>.</span></span> <span data-ttu-id="b0cbc-114">Üzerinde ayarlanmış özelliklerinden <xref:System.Windows.Controls.ContentPresenter> olduğu <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", bu denetim için erişim anahtarı belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-114">One of the properties that you can set on the <xref:System.Windows.Controls.ContentPresenter> is <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true", which you can use to specify an access key for the control.</span></span>  
  
 <span data-ttu-id="b0cbc-115">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Label> sahip bir erişim anahtarı ve metin kaydırmayı desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-115">The following example shows how to create a <xref:System.Windows.Controls.Label> that has an access key and supports text wrapping.</span></span> <span data-ttu-id="b0cbc-116">Metin kaydırmayı, örnek etkinleştirmek için <xref:System.Windows.Controls.AccessText.TextWrapping%2A> özelliği ve kullanımları altı çizili karakter erişim anahtarı belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-116">To enable text wrapping, the example sets the <xref:System.Windows.Controls.AccessText.TextWrapping%2A> property and uses an underline character to specify the access key.</span></span> <span data-ttu-id="b0cbc-117">(Alt çizgi karakteri hemen izleyen karakterin erişim anahtarıdır.)</span><span class="sxs-lookup"><span data-stu-id="b0cbc-117">(The character that immediately follows the underline character is the access key.)</span></span>  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b0cbc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0cbc-118">See also</span></span>
- [<span data-ttu-id="b0cbc-119">Nasıl yapılır: Bir etiket için Target özelliği ayarlama</span><span class="sxs-lookup"><span data-stu-id="b0cbc-119">How to: Set the Target Property of a Label</span></span>](https://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
