---
title: "İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma"
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
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31806d3ed13776e26634914b48bc887297ea4dab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>İzlenecek yol: Windows Forms DataGridView Denetiminde Sanal Modu Çalıştırma
Çok büyük miktarda tablo verilerin görüntülemek istediğinizde bir <xref:System.Windows.Forms.DataGridView> ayarlayabileceğiniz denetimi <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğine `true` ve açıkça kendi veri deposu denetimin etkileşim yönetin. Bu, bu durumda denetim performansını ince ayar sağlar.  
  
 <xref:System.Windows.Forms.DataGridView> Denetimi, bir özel veri deposuyla etkileşime geçmesini işleyebilir çeşitli olaylarını sağlar. Bu kılavuzda bu olay işleyicileri uygulama işleminde size rehberlik eder. Bu konuda aşağıdaki kod örneğinde çok basit veri kaynağı gösterim amaçları için kullanır. Bir üretim ortamında genellikle yalnızca bir önbelleğine görüntülemek ve işlemek için ihtiyacınız satırları yükleyeceğiniz <xref:System.Windows.Forms.DataGridView> etkileşim ve önbellek güncelleştirmek için olaylar. Daha fazla bilgi için bkz: [Just-In-Time verileri yüklenirken Windows Forms DataGridView denetiminde ile sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Bu konuda tek bir liste olarak kodu kopyalamak için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Form Oluşturma  
  
#### <a name="to-implement-virtual-mode"></a>Sanal mod uygulamak için  
  
1.  Türeyen bir sınıf oluşturun <xref:System.Windows.Forms.Form> ve içeren bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
     Aşağıdaki kod, bazı temel başlatma içerir. Sonraki adımlarda kullanılacak olan bazı değişkenler bildirilmektedir, sağlayan bir `Main` yöntemi ve sınıf oluşturucu basit form düzende sağlar.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  Form için bir işleyici uygulamak <xref:System.Windows.Forms.Form.Load> başlatır olay <xref:System.Windows.Forms.DataGridView> denetim ve veri deposu örnek değerlerle doldurur.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValueNeeded> istenen hücrenin değeri veri deposundan alır olay veya `Customer` nesne şu anda düzenleme.  
  
     Bu olay her değiştiğinde gerçekleşir <xref:System.Windows.Forms.DataGridView> denetim bir hücre boyama gerekiyor.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CellValuePushed> bir düzenlenen hücre değerini depolar olay `Customer` düzenlenen satır temsil eden nesne. Bu olay, kullanıcı hücrenin değerini değiştirme uygulayan her gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.NewRowNeeded> yeni bir olay `Customer` yeni oluşturulan bir satır temsil eden nesne.  
  
     Bu olay, yeni kayıtlar için satır kullanıcının girdiği olduğunda gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.RowValidated> yeni veya değiştirilmiş satırları veri deposuna kaydeder olay.  
  
     Bu olay, kullanıcının geçerli satır değiştiğinde gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> gösteren olay olup olmadığını <xref:System.Windows.Forms.DataGridView.CancelRowEdit> olay iki kez düzenleme modunda veya bir kez düzenleme modunda dışında ESC tuşuna basarak satır geri al kullanıcı işaret ettiğinde oluşur.  
  
     Varsayılan olarak, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> geçerli satırda hücreler sürece değiştiren satır geri al oluşur <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği ayarlanmış `true` içinde <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisi. Bu olay, yürütme kapsam çalışma zamanında belirlenir yararlıdır.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.CancelRowEdit> değerlerini atar olay `Customer` geçerli satır temsil eden nesne.  
  
     Bu olay, iki kez düzenleme modunda veya bir kez düzenleme modunda dışında ESC tuşuna basarak satır geri al kullanıcı sinyalleri oluşur. Geçerli satırda hiçbir hücreleri değiştirilmiş veya gerekiyorsa bu olay oluşmaz değerini <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> özelliği ayarlanmış `false` içinde bir <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> olay işleyicisi.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Uygulama için bir işleyici <xref:System.Windows.Forms.DataGridView.UserDeletingRow> varolan siler olay `Customer` veri deposu nesnesi veya bir kaydedilmemiş atar `Customer` yeni oluşturulan bir satır temsil eden nesne.  
  
     Her satırda bir başlık tıklayarak ve DELETE tuşuna basarak bir satır kullanıcıyı siler bu olay gerçekleşir.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Basit bir uygulama `Customers` Bu kod örneği tarafından kullanılan veri öğelerini temsil eden sınıf.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık formun beklendiği gibi davranır emin olmak için test edebilirsiniz.  
  
#### <a name="to-test-the-form"></a>Formu sınamak için  
  
-   Derleme ve uygulamayı çalıştırın.  
  
     Göreceğiniz bir <xref:System.Windows.Forms.DataGridView> denetim üç müşteri kayıtları ile doldurulur. Bir satır içinde birden fazla hücre değerlerini değiştirin ve iki kez düzenleme modunda ve tüm satır kendi özgün değerlerine geri döndürmek için düzenleme moduna dışında bir kez ESC tuşuna basın. Değiştirdiğinizde, ekleyin veya denetimindeki satırları silme `Customer` nesneleri veri deposunda değişiklik, eklenen veya de silinir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu uygulama, sanal modda uygulamak için tanıtıcı olayları temel bir anlayış sağlar <xref:System.Windows.Forms.DataGridView> denetim. Çeşitli yollarla temel bu uygulamada artırabilirsiniz:  
  
-   Dış veritabanı değerlerinden önbelleğe alan bir veri deposu uygulayın. Önbelleğe almak ve yalnızca küçük miktarda bellek istemci bilgisayardaki tükettikten sırasında görüntülemek için gerekli nedir içeren değerleri gerektiği gibi atmak gerekir.  
  
-   Gereksinimlerinize bağlı olarak veri deposu performansını ince ayar. Örneğin, istemci bilgisayar bellek kısıtlamaları yerine yavaş ağ bağlantıları için daha büyük bir önbellek boyutu kullanarak ve veritabanı sorguları sayısını en aza indirme dengelemek isteyebilirsiniz.  
  
 Dış veritabanı değerlerinden önbelleğe alma hakkında daha fazla bilgi için bkz [nasıl yapılır: Windows Forms DataGridView denetimini Just-In-Time veri yükleme ile sanal modu uygulama](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [Performans ayarlama Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView denetimini ölçeklendirme için en iyi uygulamalar](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Tam zamanında veri Windows Forms DataGridView denetiminde yükleme ile sanal modu uygulama](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [Nasıl yapılır: sanal modu Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
