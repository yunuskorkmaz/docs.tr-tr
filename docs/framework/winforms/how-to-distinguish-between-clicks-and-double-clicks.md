---
title: 'Nasıl yapılır: Tıklamalar ve Çift Tıklamaları Birbirinden Ayırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 84d085700091c4e7b8658e8eac4cf86fbd7730d5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070998"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Nasıl yapılır: Tıklamalar ve Çift Tıklamaları Birbirinden Ayırma
Genellikle, tek bir *tıklayın* bir kullanıcı arabirimi (UI) eylemi başlatır ve *çift* eylemi genişletir. Örneğin, tek bir tıklamayla, genellikle bir öğe seçer ve bir öğeye çift düzenler. Ancak, Windows Forms tıklama olayları bağlı bir eylem olduğundan kolayca burada bir tıklayın ve bir çift gerçekleştirmek uyumsuz eylemleri bir senaryo karşılayacak değil <xref:System.Windows.Forms.Control.Click> veya <xref:System.Windows.Forms.Control.MouseClick> olay için bağlıeylemindenöncegerçekleştirilir<xref:System.Windows.Forms.Control.DoubleClick>veya <xref:System.Windows.Forms.Control.MouseDoubleClick> olay. Bu konuda, bu sorunun iki çözümü gösterilir. Tek bir çözüm, çift tıklama olayı işlemek ve eylemleri click olay işlemede geri alma oluşturmaktır. Nadir durumlarda, tıklayın benzetimini gerçekleştirmek ve davranışı işleyerek çift gerekebilir <xref:System.Windows.Forms.Control.MouseDown> olay ve kullanarak <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> ve <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> özelliklerini <xref:System.Windows.Forms.SystemInformation> sınıfı. Tıklama ve ikinci tıklama önce değerini oluşursa arasındaki süreyi ölçmek <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> ulaşıldığında ve tıklayarak tarafından tanımlanan dikdörtgen içindeki <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, çift tıklatma eylemi gerçekleştirir; Aksi takdirde, tıklatma eylemi gerçekleştirin.  
  
### <a name="to-roll-back-a-click-action"></a>Bir tıklatma eylemi geri almak için  
  
-   Birlikte çalıştığınız denetim standart olduğundan emin olun davranışı çift tıklayın. Aksi takdirde, denetimle etkinleştirme <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi. Çift tıklatma olayını işlemek ve çift tıklatma eylemi yanı sıra tıklatma eylemi geri alma. Aşağıdaki kod örneğinde gösterilmiştir çift tıklatma eylemi, çift tıklama olayı işleme kodunu geri almak nasıl yanı sıra etkin ile özel düğme oluşturmak için.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>MouseDown olayı tıklamayla ayırt etmek için  
  
-   Tanıtıcı <xref:System.Windows.Forms.Control.MouseDown> olay ve uygun kullanarak tıklama zaman ve konum span belirlemek <xref:System.Windows.Forms.SystemInformation> özellikleri ve <xref:System.Windows.Forms.Timer> bileşeni. Olup bir ya da çift gerçekleşmeden bağlı olarak uygun eylemi gerçekleştirin. Aşağıdaki kod örneği, bu nasıl yapılabilir gösterir.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Bu örnekler komut satırından Visual Basic veya Visual C# için oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örneklerde Visual Studio kodu yeni projelere yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
