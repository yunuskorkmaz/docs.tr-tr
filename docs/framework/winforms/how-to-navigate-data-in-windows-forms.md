---
title: "Nasıl yapılır: Windows Forms'ta verilerde gezinme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 920f6d6206a8f33a912d8a7d1b46a3047ed874bc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725343"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta verilerde gezinme
Bir Windows uygulamasında bağlamak için bir veri kaynağındaki kayıtları gezinmek için en kolay yolu olan bir <xref:System.Windows.Forms.BindingSource> veri kaynağı ve ardından bağlama denetimlerini bileşen <xref:System.Windows.Forms.BindingSource>. Daha sonra üzerinde yerleşik gezinti yöntemi kullanabilirsiniz <xref:System.Windows.Forms.BindingSource> böyle bir <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> ve <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Bu yöntemleri kullanarak ayarlamak <xref:System.Windows.Forms.BindingSource.Position%2A> ve <xref:System.Windows.Forms.BindingSource.Current%2A> özelliklerini <xref:System.Windows.Forms.BindingSource> uygun şekilde. Ayrıca bir öğeyi bulmak ve ayarlayarak geçerli öğesi olarak ayarla <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Bir veri kaynağı konumu artırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği <xref:System.Windows.Forms.BindingSource> ilişkili verilerinizin kayıt konumuna gidin. Kullanarak aşağıdaki örnekte gösterildiği <xref:System.Windows.Forms.BindingSource.MoveNext%2A> yöntemi <xref:System.Windows.Forms.BindingSource> Artım yapılacağını <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği olduğunda `nextButton` tıklandığında. <xref:System.Windows.Forms.BindingSource> İlişkili olduğu `Customers` tablosunu bir veri kümesinin `Northwind`.  
  
    > [!NOTE]
    >  Ayarı <xref:System.Windows.Forms.BindingSource.Position%2A> ilk veya son kaydını dışında bir değere neden bir hata olarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] konum listesi sınırları dışında bir değere ayarlamak izin vermez. Uygulamanızda ilk veya son kaydını ilerlemiş olup olmadığını bilmek önemlidir, veri öğesi sayısı aşarsanız olup olmadığını sınamak için mantığı içerir.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Başlangıç ve bitiş geçip geçmediğini kontrol etmek için  
  
1.  İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.BindingSource.PositionChanged> olay. İşleyicisinde gerçek veri öğesi sayısı önerilen konum değerini aştı olup olmadığını test edebilirsiniz.  
  
     Aşağıdaki örnek nasıl son veri öğesi ulaştınız olup olmadığını sınayabilirsiniz gösterir. Örnekte, son öğe varsa, **sonraki** formundaki düğmesi devre dışıdır.  
  
    > [!NOTE]
    >  Değiştirdiğiniz kodda gezinme, liste, yeniden etkinleştirmeniz gerekir, dikkat **sonraki** düğmesi, böylece kullanıcılar yeni liste tüm uzunluğu göz atabilirsiniz. Ayrıca, dikkat, yukarıdaki <xref:System.Windows.Forms.BindingSource.PositionChanged> belirli olay <xref:System.Windows.Forms.BindingSource> kendi olay işleme yöntemi ile ilişkilendirilmesi gerekiyor çalıştığınız. İşleme için bir yöntemin bir örneği verilmiştir <xref:System.Windows.Forms.BindingSource.PositionChanged> olay:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Öğeyi bulup geçerli öğesi olarak ayarla  
  
1.  Geçerli öğe ayarlamak istediğiniz kaydı bulun. Bunu kullanarak yapabilirsiniz <xref:System.Windows.Forms.BindingSource.Find%2A> yöntemi <xref:System.Windows.Forms.BindingSource>uygular, veri kaynağı, <xref:System.ComponentModel.IBindingList>. Bazı örnekler veri kaynakları uygulayan <xref:System.ComponentModel.IBindingList> olan <xref:System.ComponentModel.BindingList%601> ve <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms Tarafından Desteklenen Veri Kaynakları](data-sources-supported-by-windows-forms.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
