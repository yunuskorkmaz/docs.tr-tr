---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
description: Bir Windows Presentation Foundation uygulamasında metin kutusu denetimindeki metinlerin her değiştiğinde bir yöntemi çalıştırmak için TextChanged olayını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166226"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="670c0-103">Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama</span><span class="sxs-lookup"><span data-stu-id="670c0-103">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="670c0-104">Bu örnek, bir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> denetimdeki metnin değiştiği her seferinde yöntemi yürütmek için olayı kullanmanın bir yolunu gösterir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="670c0-104">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="670c0-105">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Değişiklik için izlemek istediğiniz denetimi içeren için arka plan kod sınıfında <xref:System.Windows.Controls.TextBox> , olay her tetiklendiğinde çağrılacak bir yöntem ekleyin <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .</span><span class="sxs-lookup"><span data-stu-id="670c0-105">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="670c0-106">Bu yöntem, temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="670c0-106">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="670c0-107">Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="670c0-107">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="670c0-108">Bu olay <xref:System.Windows.Controls.TextBox> Denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="670c0-108">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="670c0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="670c0-109">Example</span></span>

<span data-ttu-id="670c0-110">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Denetiminizi tanımlayan öğesinde, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay işleyicisi yöntem adıyla eşleşen bir değere sahip özniteliği belirtin.</span><span class="sxs-lookup"><span data-stu-id="670c0-110">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="670c0-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="670c0-111">Example</span></span>

<span data-ttu-id="670c0-112">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Değişiklik için izlemek istediğiniz denetimi içeren için arka plan kod sınıfında <xref:System.Windows.Controls.TextBox> , olay her tetiklendiğinde çağrılacak bir yöntem ekleyin <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> .</span><span class="sxs-lookup"><span data-stu-id="670c0-112">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="670c0-113">Bu yöntem, temsilci tarafından beklenildiği ile eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="670c0-113">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="670c0-114">Olay işleyicisi, <xref:System.Windows.Controls.TextBox> denetimin içeriği kullanıcı veya program aracılığıyla değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="670c0-114">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="670c0-115">Bu olay <xref:System.Windows.Controls.TextBox> Denetim oluşturulduğunda ve başlangıçta metin ile doldurulduğunda ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="670c0-115">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="670c0-116">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="670c0-116">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="670c0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="670c0-117">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="670c0-118">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="670c0-118">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="670c0-119">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="670c0-119">RichTextBox Overview</span></span>](richtextbox-overview.md)
