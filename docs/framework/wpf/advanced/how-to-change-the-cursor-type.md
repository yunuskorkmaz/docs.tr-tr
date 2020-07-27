---
title: 'Nasıl yapılır: İmleç Türünü Değiştirme'
description: Öğe için fare işaretçisi Imlecini ve Windows Presentation Foundation bir uygulama için değiştirin. Bu örnek XAML ve arka plan kod dosyasından oluşur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165964"
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="f849e-104">Nasıl yapılır: İmleç Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f849e-104">How to: Change the Cursor Type</span></span>
<span data-ttu-id="f849e-105">Bu örnek, <xref:System.Windows.Input.Cursor> fare işaretçisinin belirli bir öğe ve uygulama için nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f849e-105">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="f849e-106">Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve arka plan kod dosyasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="f849e-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f849e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f849e-107">Example</span></span>  
 <span data-ttu-id="f849e-108">İstenen kullanıcı arabirimi, <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Input.Cursor> <xref:System.Windows.Controls.RadioButton> imleç değişikliğinin yalnızca tek bir öğe için geçerli olduğunu veya tüm uygulama için geçerli olduğunu ya da <xref:System.Windows.Controls.Border> Yeni imlecin uygulandığı öğeyi belirleyen bir nesne çiftini seçmek için bir, bir dizi nesnenin oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f849e-108">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="f849e-109">Aşağıdaki kod arkasında, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> imleç türü değiştiğinde çağrılan bir olay işleyicisi oluşturulur <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="f849e-109">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="f849e-110">Switch ifadesinin imleci, imleç adı üzerinde filtreler ve <xref:System.Windows.FrameworkElement.Cursor%2A> ' de <xref:System.Windows.Controls.Border> *DisplayArea*olarak adlandırılan özelliği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f849e-110">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="f849e-111">İmleç değişikliği "tüm uygulama" olarak ayarlandıysa, <xref:System.Windows.Input.Mouse.OverrideCursor%2A> özelliği <xref:System.Windows.FrameworkElement.Cursor%2A> denetimin özelliğine ayarlanır <xref:System.Windows.Controls.Border> .</span><span class="sxs-lookup"><span data-stu-id="f849e-111">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="f849e-112">Bu, imleci uygulamanın tamamına göre değiştirmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="f849e-112">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="f849e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f849e-113">See also</span></span>

- [<span data-ttu-id="f849e-114">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f849e-114">Input Overview</span></span>](input-overview.md)
