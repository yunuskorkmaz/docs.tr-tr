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
# <a name="how-to-implement-the-itypedlist-interface"></a>Nasıl yapılır: Itypedlist arabirimini uygulama
Uygulama <xref:System.ComponentModel.ITypedList> bağlanabilir bir listesi için şema bulunmasını etkinleştirmek için arabirim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.ITypedList> arabirimi. Adlı bir genel tür `SortableBindingList` türetildiği <xref:System.ComponentModel.BindingList%601> sınıf ve uyguladığı <xref:System.ComponentModel.ITypedList> arabirimi. Adlı basit bir sınıf `Customer` üstbilgisi için bağlı veri sağlayan bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
