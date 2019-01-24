---
title: 'Nasıl yapılır: Itypedlist arabirimini uygulama'
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
ms.openlocfilehash: 3d12c0b82d9475981d0c72f082665b11135d8bb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562174"
---
# <a name="how-to-implement-the-itypedlist-interface"></a><span data-ttu-id="ed436-102">Nasıl yapılır: Itypedlist arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="ed436-102">How to: Implement the ITypedList Interface</span></span>
<span data-ttu-id="ed436-103">Uygulama <xref:System.ComponentModel.ITypedList> bağlanabilir bir listesi için şema bulunmasını etkinleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="ed436-103">Implement the <xref:System.ComponentModel.ITypedList> interface to enable discovery of the schema for a bindable list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed436-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed436-104">Example</span></span>  
 <span data-ttu-id="ed436-105">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ed436-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="ed436-106">Adlı bir genel tür `SortableBindingList` türetildiği <xref:System.ComponentModel.BindingList%601> sınıf ve uyguladığı <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ed436-106">A generic type named `SortableBindingList` derives from the <xref:System.ComponentModel.BindingList%601> class and implements the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="ed436-107">Adlı basit bir sınıf `Customer` üstbilgisi için bağlı veri sağlayan bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ed436-107">A simple class named `Customer` provides data, which is bound to the header of a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ed436-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ed436-108">Compiling the Code</span></span>  
 <span data-ttu-id="ed436-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ed436-109">This example requires:</span></span>  
  
-   <span data-ttu-id="ed436-110">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="ed436-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed436-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed436-111">See also</span></span>
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="ed436-112">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ed436-112">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
