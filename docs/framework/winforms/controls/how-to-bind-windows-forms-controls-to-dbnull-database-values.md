---
title: 'Nasıl yapılır: Windows Forms denetimlerini DBNull veritabanı değerlerine bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 0c0768b922133fa0be1c8a56b4481048d1e200ba
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713793"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Nasıl yapılır: Windows Forms denetimlerini DBNull veritabanı değerlerine bağlama
Bir veri kaynağı ve veri kaynağı için Windows Forms denetimleri bağladığınızda döndürür bir <xref:System.DBNull> değeri bölümünün yerine uygun değeri işleme, biçimlendirme veya ayrıştırma olayları olmadan. <xref:System.Windows.Forms.Binding.NullValue%2A> Özelliği tarafından dönüştürülür <xref:System.DBNull> biçimlendirme veya ayrıştırma veri kaynağı değerleri belirtilen bir nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl bağlanacağını gösterir. bir <xref:System.DBNull> iki farklı durumlarda değeri. İlk nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Forms.Binding.NullValue%2A> bir dize özelliği için; ikinci nasıl ayarlanacağı gösterilmektedir. <xref:System.Windows.Forms.Binding.NullValue%2A> bir resim özelliği için.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 İlişkili özelliğin türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olmalıdır veya hataya neden olur ve başka <xref:System.Windows.Forms.Binding.NullValue%2A> değerleri işlenmeyecek. Bu durumda, bir özel durum değil.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Hataları ve ortaya çıkan özel durumlar veri bağlama ile işleme](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
