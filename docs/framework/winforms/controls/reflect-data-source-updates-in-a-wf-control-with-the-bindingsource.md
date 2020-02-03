---
title: BindingSource ile denetimdeki veri kaynağı güncelleştirmelerini yansıtma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: f98296b477dbb674cdbdbd8d03e291dd6ca0c8a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742444"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="b2a8e-102">Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma</span><span class="sxs-lookup"><span data-stu-id="b2a8e-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="b2a8e-103">Veriye dayalı denetimler kullandığınızda, veri kaynağı liste değiştirme olaylarını yükseltmezse bazen veri kaynağındaki değişikliklere yanıt vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b2a8e-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="b2a8e-104">Veri kaynağınızı bir Windows Forms denetimine bağlamak için <xref:System.Windows.Forms.BindingSource> bileşenini kullandığınızda, <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemini çağırarak veri kaynağınızın değiştiği denetime bildirimde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="b2a8e-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2a8e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2a8e-105">Example</span></span>  
 <span data-ttu-id="b2a8e-106">Aşağıdaki kod örneği, veri kaynağındaki bir güncelleştirmeyle ilgili bir denetim hakkında bildirim almak için <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> yöntemi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2a8e-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2a8e-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b2a8e-107">Compiling the Code</span></span>  
 <span data-ttu-id="b2a8e-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b2a8e-108">This example requires:</span></span>  
  
- <span data-ttu-id="b2a8e-109">System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="b2a8e-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a8e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a8e-110">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b2a8e-111">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="b2a8e-111">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="b2a8e-112">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="b2a8e-112">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
