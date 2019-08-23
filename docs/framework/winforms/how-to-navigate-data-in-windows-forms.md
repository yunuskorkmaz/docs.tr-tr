---
title: 'Nasıl yapılır: Windows Forms Verilerinde Gezinme'
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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964271"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Nasıl yapılır: Windows Forms Verilerinde Gezinme
Bir Windows uygulamasında, bir veri kaynağındaki kayıtlar arasında gezinmenin en kolay yolu, bir <xref:System.Windows.Forms.BindingSource> bileşeni veri kaynağına bağlamak ve sonra denetimleri <xref:System.Windows.Forms.BindingSource>öğesine bağlamanız. Daha <xref:System.Windows.Forms.BindingSource> sonra, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>ve <xref:System.Windows.Forms.BindingSource.MoveNext%2A> gibiyerleşik<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>Gezintiyönteminikullanabilirsiniz. <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> Bu yöntemlerin kullanılması <xref:System.Windows.Forms.BindingSource.Position%2A> <xref:System.Windows.Forms.BindingSource> uygun şekilde ve <xref:System.Windows.Forms.BindingSource.Current%2A> özelliklerini ayarlayacaktır. Ayrıca, bir öğeyi bulabilir ve <xref:System.Windows.Forms.BindingSource.Position%2A> özelliğini ayarlayarak geçerli öğe olarak ayarlayabilirsiniz.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Bir veri kaynağındaki konumu artırmak için  
  
1. Bağlantılı verilerinizin <xref:System.Windows.Forms.BindingSource> özelliğini, gidilecek kayıt konumuna ayarlayın. <xref:System.Windows.Forms.BindingSource.Position%2A> Aşağıdaki örnek <xref:System.Windows.Forms.BindingSource.MoveNext%2A> , tıklandığında <xref:System.Windows.Forms.BindingSource.Position%2A> özelliğini <xref:System.Windows.Forms.BindingSource> artırmakiçinöğesininyöntemininkullanımınıgösterir.`nextButton` , <xref:System.Windows.Forms.BindingSource> Bir veri `Customers` kümesinin`Northwind`tablosuyla ilişkilendirilir.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.Position%2A> Özelliğin ilk veya son kaydın ötesinde bir değere ayarlanması, .NET Framework konumu listenin sınırları dışındaki bir değere ayarlamanıza izin vermediğinden hata ile sonuçlanır. Uygulamanızda ilk veya son kaydın geçmiş olduğunu bildirmek için önemliyse, veri öğesi sayısını aşıp aşmayacağını test etmek için mantığı ekleyin.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Sonunu veya başlangıcını mi geçtiğini denetlemek için  
  
1. <xref:System.Windows.Forms.BindingSource.PositionChanged> Olay için bir olay işleyicisi oluşturun. İşleyicide, önerilen konum değerinin gerçek veri öğesi sayısını aşmadığını test edebilirsiniz.  
  
     Aşağıdaki örnek, son veri öğesine ulaştığınızdan nasıl test kullanabileceğinizi gösterir. Örnekte, son öğe ise, formdaki bir **sonraki** düğme devre dışı bırakılır.  
  
    > [!NOTE]
    > Kodda gezinmekte olduğunuz listeyi değiştirmeniz gerektiğine dikkat edin, kullanıcılar yeni listenin tüm uzunluğuna göz atabilmeleri için **İleri** düğmesini yeniden etkinleştirmeniz gerektiğini unutmayın. Ayrıca, üzerinde çalıştığınız özel <xref:System.Windows.Forms.BindingSource.PositionChanged> <xref:System.Windows.Forms.BindingSource> için yukarıdaki olayın olay işleme yöntemiyle ilişkilendirilmesi gerektiğini unutmayın. Aşağıda, <xref:System.Windows.Forms.BindingSource.PositionChanged> olayı işleme yöntemine bir örnek verilmiştir:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Bir öğeyi bulmak ve geçerli öğe olarak ayarlamak için  
  
1. Geçerli öğe olarak ayarlamak istediğiniz kaydı bulun. Veri kaynağınız uygularsa <xref:System.Windows.Forms.BindingSource.Find%2A> <xref:System.ComponentModel.IBindingList>, bunu yöntemini <xref:System.Windows.Forms.BindingSource>kullanarak yapabilirsiniz. Uygulayan <xref:System.ComponentModel.IBindingList> verikaynaklarına<xref:System.Data.DataView>bazı örnekler ve.<xref:System.ComponentModel.BindingList%601>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Tarafından Desteklenen Veri Kaynakları](data-sources-supported-by-windows-forms.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
