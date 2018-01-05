---
title: "Nasıl yapılır: Windows Formlarında Verilerde Gezinme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d99d794164307cb22c5dfc89d6c9c227aa457a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Verilerde Gezinme
Bir Windows uygulamasında bağlamak için bir veri kaynağındaki kayıtlarını gezinmek için en kolay yolu olan bir <xref:System.Windows.Forms.BindingSource> veri kaynağı ve ardından bağlama denetimlerine bileşen <xref:System.Windows.Forms.BindingSource>. Sonra yerleşik gezinti yöntemi kullanabileceğinizi <xref:System.Windows.Forms.BindingSource> böyle bir <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> ve <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Bu yöntemleri kullanarak ayarlamak <xref:System.Windows.Forms.BindingSource.Position%2A> ve <xref:System.Windows.Forms.BindingSource.Current%2A> özelliklerini <xref:System.Windows.Forms.BindingSource> uygun şekilde. Ayrıca bir öğeyi bulur ve ayarlayarak geçerli öğesi olarak ayarla <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Bir veri kaynağı konumu artırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği <xref:System.Windows.Forms.BindingSource> ilişkili verilerinizin kayıt konumuna gidin. Aşağıdaki örnek kullanarak gösterilmektedir <xref:System.Windows.Forms.BindingSource.MoveNext%2A> yöntemi <xref:System.Windows.Forms.BindingSource> artırmak <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği zaman `nextButton` tıklandığında. <xref:System.Windows.Forms.BindingSource> İle ilişkili `Customers` tablo bir veri kümesinin `Northwind`.  
  
    > [!NOTE]
    >  Ayarı <xref:System.Windows.Forms.BindingSource.Position%2A> özelliği ilk veya son kaydı dışında bir değere neden olmaz hata olarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] konumu liste sınırları dışında bir değere ayarlamak izin vermez. Uygulamanızda ilk veya son kaydı ilerlemiş olup olmadığını bilmek önemlidir, veri öğesi sayısı aşacak olup olmadığını sınamak için mantık ekleyin.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Başlangıç ve bitiş geçirilen olup olmadığını denetlemek için  
  
1.  İçin bir olay işleyicisi oluşturun <xref:System.Windows.Forms.BindingSource.PositionChanged> olay. İşleyicisinde önerilen konum değerini gerçek veri öğesi sayısı aştı olup olmadığını sınayabilirsiniz.  
  
     Aşağıdaki örnek, son veri öğesini ulaştınız olup olmadığını nasıl sınayabilirsiniz gösterilmektedir. Son öğesi, varsa örnekte **sonraki** formundaki düğmesi devre dışıdır.  
  
    > [!NOTE]
    >  , Değişikliği kodda gezinme, liste, yeniden etkinleştirmeniz gerekir, unutmayın **sonraki** düğmesi, böylece kullanıcılar yeni liste tüm uzunluğu göz atabilirsiniz. Ayrıca, unutmayın, yukarıdaki <xref:System.Windows.Forms.BindingSource.PositionChanged> belirli olay <xref:System.Windows.Forms.BindingSource> kendi olay işleme yöntemi ile ilişkilendirilmesi gerekiyor çalıştığınız. Aşağıdaki işleme için bir yöntem örneğidir <xref:System.Windows.Forms.BindingSource.PositionChanged> olay:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Bir öğeyi bulur ve geçerli öğesi olarak ayarlamak için  
  
1.  Geçerli öğesi olarak ayarlamak ister kaydı bulun. Kullanarak bunu yapabilirsiniz <xref:System.Windows.Forms.BindingSource.Find%2A> yöntemi <xref:System.Windows.Forms.BindingSource>uygular, veri kaynağı, <xref:System.ComponentModel.IBindingList>. Bazı örnekler veri kaynakları uygulayan <xref:System.ComponentModel.IBindingList> olan <xref:System.ComponentModel.BindingList%601> ve <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Tarafından Desteklenen Veri Kaynakları](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Windows Forms Veri Bağlamada Bildirimi Değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Veri Bağlama ve Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)
