---
title: 'Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme'
description: İletiler bir denetime ulaşmadan önce, form düzeyinde Windows Forms klavye girişini nasıl işleyeceğinizi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904162"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="6736e-103">Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme</span><span class="sxs-lookup"><span data-stu-id="6736e-103">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="6736e-104">Windows Forms, iletiler bir denetime ulaşmadan önce klavye iletilerini form düzeyinde işleme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6736e-104">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="6736e-105">Bu konu, bu görevin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6736e-105">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="6736e-106">Bir klavye iletisini form düzeyinde işlemek için</span><span class="sxs-lookup"><span data-stu-id="6736e-106">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="6736e-107"><xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> Başlangıç formunun veya olayını işleyin ve form özelliğini, form <xref:System.Windows.Forms.Form.KeyPreview%2A> `true` üzerinde herhangi bir denetime erişmeden önce form tarafından alınan klavye iletilerini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6736e-107">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="6736e-108">Aşağıdaki kod örneği, <xref:System.Windows.Forms.Control.KeyPress> Tüm sayı anahtarlarını algılayarak ve ' 1 ', ' 4 ' ve ' 7 ' kullanan olayı işler.</span><span class="sxs-lookup"><span data-stu-id="6736e-108">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="6736e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6736e-109">Example</span></span>  
 <span data-ttu-id="6736e-110">Aşağıdaki kod örneği, yukarıdaki örnek için tüm uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="6736e-110">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="6736e-111">Uygulama <xref:System.Windows.Forms.TextBox> , odağı içinden taşımanızı sağlayan diğer birçok denetim ile birlikte içerir <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="6736e-111">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="6736e-112"><xref:System.Windows.Forms.Control.KeyPress>Ana <xref:System.Windows.Forms.Form> ' 1 ', ' 4 ' ve ' 7 ' kullanımını ve <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.TextBox> geri kalan anahtarları görüntülerken ' 2 ', ' 5 ' ve ' 8 ' kullanımını tüketen olay.</span><span class="sxs-lookup"><span data-stu-id="6736e-112">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="6736e-113"><xref:System.Windows.Forms.MessageBox>Bir sayı tuşuna bastığınızda çıktıyı karşılaştırın, ancak <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.MessageBox> odak diğer denetimlerden birinde olduğunda bir sayı tuşuna bastığınızda çıkış ile odak edilir.</span><span class="sxs-lookup"><span data-stu-id="6736e-113">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6736e-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6736e-114">Compiling the Code</span></span>  
 <span data-ttu-id="6736e-115">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6736e-115">This example requires:</span></span>  
  
- <span data-ttu-id="6736e-116">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6736e-116">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6736e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6736e-117">See also</span></span>

- [<span data-ttu-id="6736e-118">Bir Windows Forms Uygulamasında Klavye Girdisi</span><span class="sxs-lookup"><span data-stu-id="6736e-118">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
