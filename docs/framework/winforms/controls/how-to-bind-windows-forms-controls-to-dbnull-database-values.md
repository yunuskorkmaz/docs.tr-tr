---
title: 'Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 8abce5d69a7cece6528e0c9d8728de0e0acd9305
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591421"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama
Bir veri kaynağı ve veri kaynağı için Windows Forms denetimleri bağladığınızda döndürür bir <xref:System.DBNull> değeri bölümünün yerine uygun değeri işleme, biçimlendirme veya ayrıştırma olayları olmadan. <xref:System.Windows.Forms.Binding.NullValue%2A> Özelliği tarafından dönüştürülür <xref:System.DBNull> biçimlendirme veya ayrıştırma veri kaynağı değerleri belirtilen bir nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.DBNull> iki farklı durumlarda değeri. İlk nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Forms.Binding.NullValue%2A> bir dize özelliği için; ikinci nasıl ayarlanacağı gösterilmektedir. <xref:System.Windows.Forms.Binding.NullValue%2A> bir resim özelliği için.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 İlişkili özelliğin türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olmalıdır veya hataya neden olur ve başka <xref:System.Windows.Forms.Binding.NullValue%2A> değerleri işlenmeyecek. Bu durumda, bir özel durum değil.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Hataları ve ortaya çıkan özel durumlar veri bağlama ile işleme](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
