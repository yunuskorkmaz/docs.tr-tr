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
ms.openlocfilehash: 2463a9c77a9836ff251e799056cc5131bf6c99e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61800864"
---
# <a name="how-to-implement-the-itypedlist-interface"></a><span data-ttu-id="a0262-102">Nasıl yapılır: ITypedList Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="a0262-102">How to: Implement the ITypedList Interface</span></span>
<span data-ttu-id="a0262-103">Uygulama <xref:System.ComponentModel.ITypedList> bağlanabilir bir listesi için şema bulunmasını etkinleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="a0262-103">Implement the <xref:System.ComponentModel.ITypedList> interface to enable discovery of the schema for a bindable list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0262-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0262-104">Example</span></span>  
 <span data-ttu-id="a0262-105">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a0262-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="a0262-106">Adlı bir genel tür `SortableBindingList` türetildiği <xref:System.ComponentModel.BindingList%601> sınıf ve uyguladığı <xref:System.ComponentModel.ITypedList> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a0262-106">A generic type named `SortableBindingList` derives from the <xref:System.ComponentModel.BindingList%601> class and implements the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="a0262-107">Adlı basit bir sınıf `Customer` üstbilgisi için bağlı veri sağlayan bir <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a0262-107">A simple class named `Customer` provides data, which is bound to the header of a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0262-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a0262-108">Compiling the Code</span></span>  
 <span data-ttu-id="a0262-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a0262-109">This example requires:</span></span>  
  
- <span data-ttu-id="a0262-110">System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="a0262-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0262-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0262-111">See also</span></span>

- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="a0262-112">Veri Bağlama ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a0262-112">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
