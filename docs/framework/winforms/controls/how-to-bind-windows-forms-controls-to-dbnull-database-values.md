---
title: Denetimleri DBNull veritabanı değerlerine bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746670"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama
Windows Forms denetimleri bir veri kaynağına bağladığınızda ve veri kaynağı bir <xref:System.DBNull> değeri döndürürse, olayları işleme, biçimlendirme veya ayrıştırma olaylarını kullanmadan uygun bir değeri değiştirebilirsiniz. <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği, veri kaynağı değerlerini biçimlendirirken veya ayrıştırırken belirtilen bir nesneye <xref:System.DBNull> dönüştürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki farklı durumda <xref:System.DBNull> bir değerin nasıl bağlanacağını gösterir. İlki, bir dize özelliği için <xref:System.Windows.Forms.Binding.NullValue%2A> ayarlamayı gösterir; İkincisi, bir görüntü özelliği için <xref:System.Windows.Forms.Binding.NullValue%2A> ayarlamayı gösterir.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Bağlantılı özelliğin türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olmalıdır veya hata oluşur, başka bir <xref:System.Windows.Forms.Binding.NullValue%2A> değeri işlenmeyecek. Bu durumda, bir özel durum oluşturulmaz.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
