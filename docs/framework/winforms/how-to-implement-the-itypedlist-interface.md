---
title: 'Nasıl yapılır: ITypedList Arabirimini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ITypedList interface
- BindingList(Of T) class
- data binding [Windows Forms], implementing
- IBindingList interface
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
ms.openlocfilehash: 181879d3e41e0dd140c79a4c63d52e6999acf86d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538077"
---
# <a name="how-to-implement-the-itypedlist-interface"></a><span data-ttu-id="1e25e-102">Nasıl yapılır: ITypedList Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="1e25e-102">How to: Implement the ITypedList Interface</span></span>
<span data-ttu-id="1e25e-103">Uygulama <xref:System.ComponentModel.ITypedList> bağlanabilirse listesi için şema bulunmasını etkinleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="1e25e-103">Implement the <xref:System.ComponentModel.ITypedList> interface to enable discovery of the schema for a bindable list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e25e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e25e-104">Example</span></span>  
 <span data-ttu-id="1e25e-105">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterilen <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1e25e-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="1e25e-106">Adlı genel bir tür `SortableBindingList` türetilen <xref:System.ComponentModel.BindingList%601> sınıfı ve uygulayan <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1e25e-106">A generic type named `SortableBindingList` derives from the <xref:System.ComponentModel.BindingList%601> class and implements the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="1e25e-107">Adlı basit bir sınıf `Customer` üstbilgisi için bağlı veri sağlayan bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="1e25e-107">A simple class named `Customer` provides data, which is bound to the header of a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e25e-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1e25e-108">Compiling the Code</span></span>  
 <span data-ttu-id="1e25e-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1e25e-109">This example requires:</span></span>  
  
-   <span data-ttu-id="1e25e-110">System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1e25e-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e25e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e25e-111">See Also</span></span>  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [<span data-ttu-id="1e25e-112">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1e25e-112">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
