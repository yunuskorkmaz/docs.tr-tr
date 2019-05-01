---
title: 'Nasıl yapılır: IListSource Arabirimini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
ms.openlocfilehash: bd4e554b7e4be51847496307b50be3084d0115d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801770"
---
# <a name="how-to-implement-the-ilistsource-interface"></a><span data-ttu-id="0f7bd-102">Nasıl yapılır: IListSource Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="0f7bd-102">How to: Implement the IListSource Interface</span></span>
<span data-ttu-id="0f7bd-103">Uygulama <xref:System.ComponentModel.IListSource> arabirimi uygulamıyor bağlanabilir bir sınıf oluşturmak için <xref:System.Collections.IList> ancak bunun yerine başka bir konumdan bir liste sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f7bd-103">Implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class that does not implement <xref:System.Collections.IList> but instead provides a list from another location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f7bd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f7bd-104">Example</span></span>  
 <span data-ttu-id="0f7bd-105">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.IListSource> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0f7bd-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.IListSource> interface.</span></span> <span data-ttu-id="0f7bd-106">Adlı bir bileşen `EmployeeListSource` sunan bir <xref:System.Collections.IList> uygulayarak veri bağlama için <xref:System.ComponentModel.IListSource.GetList%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0f7bd-106">A component named `EmployeeListSource` exposes an <xref:System.Collections.IList> for data binding by implementing the <xref:System.ComponentModel.IListSource.GetList%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.IListSource#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f7bd-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0f7bd-107">Compiling the Code</span></span>  
 <span data-ttu-id="0f7bd-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0f7bd-108">This example requires:</span></span>  
  
- <span data-ttu-id="0f7bd-109">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="0f7bd-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f7bd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f7bd-110">See also</span></span>

- <xref:System.ComponentModel.IListSource>
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="0f7bd-111">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f7bd-111">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
