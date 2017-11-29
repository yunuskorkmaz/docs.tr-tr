---
title: "Nasıl Yapılır: Arka Planda Dosya İndirme"
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
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b83f5ae935ed9ba6c5351d48175ee7747e7b01b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-the-background"></a>Nasıl Yapılır: Arka Planda Dosya İndirme
Dosya indirme ortak bir görevdir ve bu büyük olasılıkla uzun süren işlem ayrı bir iş parçacığı üzerinde çalıştırmak genellikle yararlıdır. Kullanım <xref:System.ComponentModel.BackgroundWorker> çok az kod ile bu görevi gerçekleştirmek için bileşen.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösteren bir <xref:System.ComponentModel.BackgroundWorker> bir URL'den bir XML dosyası yüklemek için bileşen. Kullanıcı tıkladığında **karşıdan** düğmesini <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılarını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi bir <xref:System.ComponentModel.BackgroundWorker> bileşeni yükleme işlemini başlatmak üzere. Düğme için karşıdan yükleme süresini devre dışı ve indirme tamamlandıktan sonra etkin. A <xref:System.Windows.Forms.MessageBox> dosyasının içeriğini görüntüler.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Dosya indirme**  
  
 Dosya karşıdan yüklenir <xref:System.ComponentModel.BackgroundWorker> çalıştıran bileşenin iş parçacığı <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Kodunuzu çağırması bu iş parçacığı başladığı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Bir BackgroundWorker tamamlanması bekleniyor**  
  
 `downloadButton_Click` Olay işleyicisi bekleme gösteren bir <xref:System.ComponentModel.BackgroundWorker> zaman uyumsuz, görevini tamamlamak için bileşen.  
  
 Yalnızca uygulama olaylara yanıt vermek istiyorsanız ve arka plan iş parçacığı tamamlanmasını beklerken ana iş parçacığı içinde herhangi bir iş yapmak istiyor musunuz yalnızca işleyici çıkın.  
  
 Ana iş parçacığında iş yapmadan devam etmek istiyorsanız, kullanmak <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> belirlemek için özellik isteyip <xref:System.ComponentModel.BackgroundWorker> iş parçacığı hala çalışıyor. İndirme işlerken örnekte, bir ilerleme çubuğu güncelleştirilir. Çağırdığınızdan emin olun <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> kullanıcı Arabiriminin yanıt verebilir durumda tutmak için yöntem.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Sonuç görüntüleme**  
  
 `backgroundWorker1_RunWorkerCompleted` Yöntemi tanıtıcıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay ve arka plan işlemi tamamlandıktan sonra çağrılır. Bu yöntem ilk denetler <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliği. Varsa <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> olan `null`, sonra da bu yöntem dosyanın içeriğini görüntüler. Ardından indirme başladığındaki devre dışı bırakıldı, İndir düğmesini etkinleştirir ve ilerleme çubuğu sıfırlar.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Drawing, System.Windows.Forms ve System.Xml derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman kontrol <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğinde, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> erişmeye çalışmadan önce olay işleyicisi <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> özelliği veya tarafından etkilenmiş herhangi bir nesne <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Nasıl yapılır: bir işlemi arka planda çalıştırma](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
