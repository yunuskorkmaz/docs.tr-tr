---
title: "Nasıl yapılır: İmleç Türünü Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c59f4c90eed00775fc9fceaf872391faa93784
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-cursor-type"></a><span data-ttu-id="df524-102">Nasıl yapılır: İmleç Türünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="df524-102">How to: Change the Cursor Type</span></span>
<span data-ttu-id="df524-103">Bu örnek nasıl değiştirileceğini gösterir <xref:System.Windows.Input.Cursor> uygulama ve belirli bir öğe için fare işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="df524-103">This example shows how to change the <xref:System.Windows.Input.Cursor> of the mouse pointer for a specific element and for the application.</span></span>  
  
 <span data-ttu-id="df524-104">Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve dosyanın arkasındaki kod.</span><span class="sxs-lookup"><span data-stu-id="df524-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df524-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="df524-105">Example</span></span>  
 <span data-ttu-id="df524-106">Oluşan kullanıcı arayüzü oluşturulur bir <xref:System.Windows.Controls.ComboBox> istenen seçmek için <xref:System.Windows.Input.Cursor>, bir çift <xref:System.Windows.Controls.RadioButton> imleç değişiklik yalnızca tek bir öğe için geçerlidir tüm uygulama için geçerlidir gerekmediğini belirlemek üzere nesneleri ve bir <xref:System.Windows.Controls.Border> Yeni imlecin uygulandığı öğe olduğu.</span><span class="sxs-lookup"><span data-stu-id="df524-106">The user interface is created, which consists of a <xref:System.Windows.Controls.ComboBox> to select the desired <xref:System.Windows.Input.Cursor>, a pair of <xref:System.Windows.Controls.RadioButton> objects to determine if the cursor change applies to only a single element or applies to the entire application, and a <xref:System.Windows.Controls.Border> which is the element that the new cursor is applied to.</span></span>  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 <span data-ttu-id="df524-107">Aşağıdaki arka plan kodu oluşturur bir <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> imleç türü olarak değiştiğinde çağrılan olay işleyicisi <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="df524-107">The following code behind creates a <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event handler which is called when the cursor type is changed in the <xref:System.Windows.Controls.ComboBox>.</span></span>  <span data-ttu-id="df524-108">Switch deyimi filtreler imleç adı ve kümelerini <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği <xref:System.Windows.Controls.Border> adlı *DisplayArea*.</span><span class="sxs-lookup"><span data-stu-id="df524-108">A switch statement filters on the cursor name and sets the <xref:System.Windows.FrameworkElement.Cursor%2A> property on the <xref:System.Windows.Controls.Border> which is named *DisplayArea*.</span></span>  
  
 <span data-ttu-id="df524-109">İmleç Değiştir "Tüm uygulamayı", ayarlarsanız <xref:System.Windows.Input.Mouse.OverrideCursor%2A> özelliği ayarlanmış <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği <xref:System.Windows.Controls.Border> denetim.</span><span class="sxs-lookup"><span data-stu-id="df524-109">If the cursor change is set to "Entire Application", the <xref:System.Windows.Input.Mouse.OverrideCursor%2A> property is set to the <xref:System.Windows.FrameworkElement.Cursor%2A> property of the <xref:System.Windows.Controls.Border> control.</span></span>  <span data-ttu-id="df524-110">Bu, tüm uygulama için değiştirmek için imleci zorlar.</span><span class="sxs-lookup"><span data-stu-id="df524-110">This forces the cursor to change for the whole application.</span></span>  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a><span data-ttu-id="df524-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df524-111">See Also</span></span>  
 [<span data-ttu-id="df524-112">Girişe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="df524-112">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)
