---
title: 'İzlenecek yol: DataGridView denetiminde sanal modu uygulama'
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
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746523"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma
<xref:System.Windows.Forms.DataGridView> denetiminde çok büyük miktarlarda tablo verisi göstermek istediğinizde, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true` olarak ayarlayabilir ve denetimin kendi veri deposuyla etkileşimini açıkça yönetebilirsiniz. Bu durum, denetimin performansını bu durumda ayarlamanıza olanak sağlar.  
  
 <xref:System.Windows.Forms.DataGridView> denetimi, özel bir veri deposuyla etkileşim kurmak için işleyebilmeniz gereken çeşitli olaylar sağlar. Bu izlenecek yol, bu olay işleyicilerini uygulama sürecinde size rehberlik eder. Bu konudaki kod örneği, çizim amacıyla çok basit bir veri kaynağı kullanır. Bir üretim ayarında genellikle yalnızca bir önbellekte görüntülemesi gereken satırları yüklersiniz ve önbelleği etkileşimde bulunmak ve güncelleştirmek için <xref:System.Windows.Forms.DataGridView> olaylarını işleyebilirsiniz. Daha fazla bilgi için bkz [. Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Bu konudaki kodu tek bir liste olarak kopyalamak için, bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-implement-virtual-mode"></a>Sanal modu uygulamak için  
  
1. <xref:System.Windows.Forms.Form> türetilen ve <xref:System.Windows.Forms.DataGridView> denetimi içeren bir sınıf oluşturun.  
  
     Aşağıdaki kod, bazı temel başlatma içerir. Sonraki adımlarda kullanılacak bazı değişkenler bildirir, bir `Main` yöntemi sağlar ve sınıf oluşturucusunda basit bir form düzeni sağlar.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Formunuzun <xref:System.Windows.Forms.Form.Load> olayı için <xref:System.Windows.Forms.DataGridView> denetimini başlatan ve veri deposunu örnek değerlerle dolduran bir işleyici uygulayın.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Veri deposundan veya şu anda düzenleme aşamasında olan `Customer` nesnesinden istenen hücre değerini alan <xref:System.Windows.Forms.DataGridView.CellValueNeeded> olayı için bir işleyici uygulayın.  
  
     Bu olay, <xref:System.Windows.Forms.DataGridView> denetimi bir hücreyi boyamak gerektiğinde oluşur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Düzenlenen satırı temsil eden `Customer` nesnesinde düzenlenmiş bir hücre değerini depolayan <xref:System.Windows.Forms.DataGridView.CellValuePushed> olayı için bir işleyici uygulayın. Bu olay, Kullanıcı bir hücre değeri değişikliğini her işlediğinde oluşur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Yeni oluşturulan bir satırı temsil eden yeni bir `Customer` nesnesi oluşturan <xref:System.Windows.Forms.DataGridView.NewRowNeeded> olayı için bir işleyici uygulayın.  
  
     Bu olay, Kullanıcı her yeni kayıt için satırı girdiğinde oluşur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Yeni veya değiştirilmiş satırları veri deposuna kaydeden <xref:System.Windows.Forms.DataGridView.RowValidated> olayı için bir işleyici uygulayın.  
  
     Bu olay, Kullanıcı geçerli satırı her değiştirdiğinde oluşur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Kullanıcı satır yeniden sürümüne, düzenleme modunda veya düzenleme modunun dışında bir kez tuşlarına basarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olayının ne zaman gerçekleşeceğini belirten <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olayı için bir işleyici uygulayın.  
  
     Varsayılan olarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> geçerli satırdaki herhangi bir hücre değiştirildiğinde, <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicide `true` olarak ayarlanmadığı takdirde satır yeniden sürümünden sonra gerçekleşir. Bu olay, çalışma sırasında kayıt kapsamı saptandığı zaman yararlıdır.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Geçerli satırı temsil eden `Customer` nesnesinin değerlerini attığı <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olayı için bir işleyici uygulayın.  
  
     Bu olay, Kullanıcı, düzenleme modunda veya düzenleme modunun dışında bir kez ESC tuşuna basarak satır yeniden sürümüne işaret ediyorsa meydana gelir. Geçerli satırda hiçbir hücre değiştirilmemişse veya <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliğinin değeri bir <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisinde `false` olarak ayarlandıysa bu olay oluşmaz.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Veri deposundan var olan bir `Customer` nesnesini silen veya yeni oluşturulan bir satırı temsil eden kaydedilmemiş bir `Customer` nesnesini attığı <xref:System.Windows.Forms.DataGridView.UserDeletingRow> olayı için bir işleyici uygulayın.  
  
     Bu olay, Kullanıcı bir satır başlığına tıklayıp DELETE tuşuna basarak bir satırı sildiğinde oluşur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Bu kod örneği tarafından kullanılan veri öğelerini temsil etmek için basit bir `Customers` sınıfı uygulayın.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu test etmek için  
  
- Uygulamayı derleyin ve çalıştırın.  
  
     Üç müşteri kaydı ile doldurulmuş bir <xref:System.Windows.Forms.DataGridView> denetimi göreceksiniz. Bir satırdaki birden çok hücrenin değerlerini değiştirebilir ve tüm satırı özgün değerlerine dönüştürmek için düzenleme modunun dışında iki kez ESC tuşuna basın. Denetimdeki satırları değiştirirken, eklediğinizde veya sildiğinizde, veri deposundaki `Customer` nesneleri de değiştirilir, eklenir veya silinir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, <xref:System.Windows.Forms.DataGridView> denetiminde sanal modu uygulamak için işlemeniz gereken olayların temel bir şekilde anlaşılmasına olanak tanır. Bu temel uygulamayı çeşitli yollarla geliştirebilirsiniz:  
  
- Bir dış veritabanından değerleri önbelleğe alan bir veri deposu uygulayın. Önbellek, istemci bilgisayarda az miktarda bellek tüketirken yalnızca görüntülenmek üzere gerekli olan öğeleri içermesi için gereken değerleri alıp atmalıdır.  
  
- Gereksinimlerinize bağlı olarak veri deposunun performansını ayrıntılı olarak ayarlayın. Örneğin, daha büyük bir önbellek boyutu kullanarak ve veritabanı sorgularının sayısını en aza indirerek, istemci bilgisayar bellek sınırlamaları yerine yavaş ağ bağlantılarını dengelemek isteyebilirsiniz.  
  
 Bir dış veritabanından verileri önbelleğe alma hakkında daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme Ile sanal modu uygulama](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
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
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
