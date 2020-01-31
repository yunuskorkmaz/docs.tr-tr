---
title: 'Nasıl yapılır: verilerde gezinme'
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
ms.openlocfilehash: 2dd900b652b0ff21ea0eb0dbc5463b22c869ec7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739393"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Verilerde Gezinme
Bir Windows uygulamasında, bir veri kaynağındaki kayıtlar arasında gezinmenin en kolay yolu <xref:System.Windows.Forms.BindingSource> bir bileşeni veri kaynağına bağlamak ve sonra denetimleri <xref:System.Windows.Forms.BindingSource>bağlamanız. Daha sonra, <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> ve <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>yerleşik gezinti yöntemini kullanabilirsiniz. Bu yöntemlerin kullanılması <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.Position%2A> ve <xref:System.Windows.Forms.BindingSource.Current%2A> özelliklerini uygun şekilde ayarlayacaktır. Ayrıca, bir öğe bulabilir ve <xref:System.Windows.Forms.BindingSource.Position%2A> özelliğini ayarlayarak geçerli öğe olarak ayarlayabilirsiniz.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Bir veri kaynağındaki konumu artırmak için  
  
1. Bağlantılı verilerinizin <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.Position%2A> özelliğini, gidilecek kayıt konumuna ayarlayın. Aşağıdaki örnek, `nextButton` tıklandığında <xref:System.Windows.Forms.BindingSource.Position%2A> özelliğini artırmak için <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.MoveNext%2A> yöntemini kullanmayı gösterir. <xref:System.Windows.Forms.BindingSource>, bir veri kümesi `Northwind``Customers` tabloyla ilişkilendirilir.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.Position%2A> özelliğinin ilk veya son kaydın ötesinde bir değere ayarlanması, .NET Framework, konumu listenin sınırları dışındaki bir değere ayarlamanıza izin vermediğinden hata ile sonuçlanır. Uygulamanızda ilk veya son kaydın geçmiş olduğunu bildirmek için önemliyse, veri öğesi sayısını aşıp aşmayacağını test etmek için mantığı ekleyin.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Sonunu veya başlangıcını mi geçtiğini denetlemek için  
  
1. <xref:System.Windows.Forms.BindingSource.PositionChanged> olayı için bir olay işleyicisi oluşturun. İşleyicide, önerilen konum değerinin gerçek veri öğesi sayısını aşmadığını test edebilirsiniz.  
  
     Aşağıdaki örnek, son veri öğesine ulaştığınızdan nasıl test kullanabileceğinizi gösterir. Örnekte, son öğe ise, formdaki bir **sonraki** düğme devre dışı bırakılır.  
  
    > [!NOTE]
    > Kodda gezinmekte olduğunuz listeyi değiştirmeniz gerektiğine dikkat edin, kullanıcılar yeni listenin tüm uzunluğuna göz atabilmeleri için **İleri** düğmesini yeniden etkinleştirmeniz gerektiğini unutmayın. Ayrıca, üzerinde çalıştığınız belirli bir <xref:System.Windows.Forms.BindingSource> için yukarıdaki <xref:System.Windows.Forms.BindingSource.PositionChanged> olayının olay işleme yöntemiyle ilişkilendirilmesi gerektiğini unutmayın. Aşağıda <xref:System.Windows.Forms.BindingSource.PositionChanged> olayı işleme yöntemine bir örnek verilmiştir:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Bir öğeyi bulmak ve geçerli öğe olarak ayarlamak için  
  
1. Geçerli öğe olarak ayarlamak istediğiniz kaydı bulun. Veri kaynağınız <xref:System.ComponentModel.IBindingList>uygularsa, bunu <xref:System.Windows.Forms.BindingSource><xref:System.Windows.Forms.BindingSource.Find%2A> yöntemini kullanarak yapabilirsiniz. <xref:System.ComponentModel.IBindingList> uygulayan veri kaynaklarına bazı örnekler <xref:System.ComponentModel.BindingList%601> ve <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Tarafından Desteklenen Veri Kaynakları](data-sources-supported-by-windows-forms.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
