---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855614"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="0f776-102">Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama</span><span class="sxs-lookup"><span data-stu-id="0f776-102">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="0f776-103">Bu örnek, bir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> <xref:System.Windows.Controls.TextBox> denetimdeki metnin değiştiği her seferinde yöntemi yürütmek için olayı kullanmanın bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f776-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="0f776-104">Değişiklik için izlemek istediğiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> denetimi içeren için arka plan kod sınıfında, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay her tetiklendiğinde çağrılacak bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f776-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="0f776-105">Bu yöntem, <xref:System.Windows.Controls.TextChangedEventHandler> temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f776-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="0f776-106">Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0f776-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="0f776-107">Bu olay <xref:System.Windows.Controls.TextBox> denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="0f776-107">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="0f776-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f776-108">Example</span></span>

<span data-ttu-id="0f776-109">Denetiminizi tanımlayan öğesinde, olay işleyicisi yöntem adıyla eşleşen <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> bir değere sahip özniteliği belirtin. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="0f776-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="0f776-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f776-110">Example</span></span>

<span data-ttu-id="0f776-111">Değişiklik için izlemek istediğiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> denetimi içeren için arka plan kod sınıfında, <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay her tetiklendiğinde çağrılacak bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f776-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="0f776-112">Bu yöntem, <xref:System.Windows.Controls.TextChangedEventHandler> temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f776-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="0f776-113">Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0f776-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="0f776-114">Bu olay <xref:System.Windows.Controls.TextBox> denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="0f776-114">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="0f776-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f776-115">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="0f776-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f776-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="0f776-117">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f776-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="0f776-118">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0f776-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
