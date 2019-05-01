---
title: 'İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 7f6bf1703a6536f4d22b3a2fbe412579c59d39dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973777"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Uygulama
Çok büyük miktarda içindeki tablosal verileri görüntülemek istediğiniz zaman bir <xref:System.Windows.Forms.DataGridView> ayarlayabileceğiniz denetimi <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` ve açıkça denetimin etkileşim kendi veri deposu ile yönetin. Bu durumda denetimin performansını ayarlamanıza olanak tanır.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi, bir özel veri deposuyla etkileşime geçmesini işleyebilir çeşitli olayları sağlar. Bu izlenecek yol, bu olay işleyicileri uygulama sürecinde size yol gösterir. Bu konuda aşağıdaki kod örneğinde çok basit bir veri kaynağı için gösterim amacıyla kullanır. Bir üretim ayarında genellikle yalnızca bir önbelleğine görüntülemek ve işlemek için gereken satır yükleyecek <xref:System.Windows.Forms.DataGridView> olayları ile etkileşim kurmanızı ve önbelleğini güncelleştirin. Daha fazla bilgi için [ile tam zamanında veri yükleme Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Bu konudaki tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Sanal modu Windows Forms DataGridView denetiminde](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-implement-virtual-mode"></a>Sanal modu uygulama  
  
1. Türetilen bir sınıf oluşturmanız <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetimi.  
  
     Aşağıdaki kod, bazı temel başlatma içerir. Sonraki adımlarda kullanılacak olan bazı değişkenler bildirilmektedir, sağlayan bir `Main` yöntemi, sınıf oluşturucusu bir Basit form düzeni sağlar.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatan olay <xref:System.Windows.Forms.DataGridView> denetim ve veri deposu örnek değerlerle doldurur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValueNeeded> veri deposundan istenen hücre değerini alır. olay veya `Customer` nesnesi şu anda düzenleme.  
  
     Bu olay oluşturduğunda <xref:System.Windows.Forms.DataGridView> denetim boyama hücre gerekiyor.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValuePushed> depolayan bir düzenlenmiş hücre değerinde olay `Customer` düzenlenen satırı temsil eden nesne. Bu olay, bir hücre değerini değişiklik kullanıcı tarafından işlenen her gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.NewRowNeeded> oluşturan yeni bir olay `Customer` yeni oluşturulan bir satırı temsil eden nesne.  
  
     Bu olay, yeni kayıtlar için satır kullanıcının girdiği olduğunda gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.RowValidated> yeni veya değiştirilmiş satırları veri deposuna kaydeder olay.  
  
     Bu olay, kullanıcının geçerli satırı değiştiğinde gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> gösteren olay olup olmadığını <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olayı iki kez düzenleme modunda veya düzenleme modu dışında bir kez ESC tuşuna basarak satır geri al kullanıcı işaret ettiğinde gerçekleşir.  
  
     Varsayılan olarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> geçerli satırda hücreler sürece değişiklik sırasında satır geri al gerçekleşir <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği `true` içinde <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisi. Bu olay işleme kapsamı çalışma zamanında belirlenir yararlı olur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CancelRowEdit> değerleri atar olay `Customer` geçerli satırı temsil eden nesne.  
  
     Bu olay, iki kez düzenleme modunda veya düzenleme modu dışında bir kez ESC tuşuna basarak satır geri al kullanıcıya bildirir oluşur. Bu olay, geçerli satırda hiçbir hücreleri değiştirildiyse ya gerçekleşmez değerini <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği sınıflandırmalara ayarlandığı `false` içinde bir <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisi.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Uygulamak için bir işleyici <xref:System.Windows.Forms.DataGridView.UserDeletingRow> varolan siler olay `Customer` nesneyi veri deposundan veya bir kaydedilmemiş atar `Customer` yeni oluşturulan bir satırı temsil eden nesne.  
  
     Bu olay, her kullanıcı bir satır başlığına tıklayarak ve DELETE tuşuna basarak bir satır siler gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Basit bir uygulama `Customers` Bu kod örneği tarafından kullanılan veri öğelerini temsil eden sınıf.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Şimdi beklendiği gibi davrandığından emin olmak için form test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
- Derleme ve uygulamayı çalıştırın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim üç müşteri kayıt ile doldurulur. Bir satırdaki birden çok hücre değerlerini değiştirme ve düzenleme modunda iki kez ve orijinal değerleri için tüm satırı dönmek için düzenleme modu dışında bir kez ESC tuşuna basın. Değiştirme eklediğinizde veya denetimindeki satırları silmek `Customer` veri deposundaki nesne değiştirilmiş, eklenen veya de silinir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulamanın sanal modu uygulama işlemek olayları temel bir anlayış verir <xref:System.Windows.Forms.DataGridView> denetimi. Çeşitli yollarla temel bu uygulamada şu iyileştirmeleri yapabilir:  
  
- Bir dış veritabanından değerleri önbelleğe alan bir veri deposuna uygulayın. Önbelleğe alma ve istemci bilgisayarda küçük miktarda bellek tükettikten çalışırken görüntü için yalnızca içeren değerleri gereken şekilde atmak gerekir.  
  
- Performans gereksinimlerinize bağlı olarak veri deposunun hassas ayarlamalar yapabilirsiniz. Örneğin, istemci bilgisayarın bellek sınırlamaları yerine yavaş ağ bağlantıları için veritabanı sorguları sayısını en aza indirmek ve daha büyük bir önbellek boyutu ile telafi isteyebilirsiniz.  
  
 Bir dış veritabanından değerleri önbelleğe alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows tam zamanında veri yükleme ile sanal modu uygulama Forms DataGridView denetiminde](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
