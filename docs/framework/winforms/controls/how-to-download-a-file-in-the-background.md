---
title: 'Nasıl yapılır: Arka Planda Dosya İndirme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1d62bbac8550a5e632760e196463285e4c9a14ce
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651763"
---
# <a name="how-to-download-a-file-in-the-background"></a>Nasıl yapılır: Arka Planda Dosya İndirme
Dosya indirme genel bir görevdir ve genellikle ayrı bir iş parçacığı üzerinde olası zaman bu işlemin çalıştırılması yararlı olur. Kullanım <xref:System.ComponentModel.BackgroundWorker> çok az kod ile bu görevi gerçekleştirmek için bileşen.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir. bir <xref:System.ComponentModel.BackgroundWorker> bileşen bir URL'den XML dosyası yüklenemedi. Kullanıcı tıkladığında **indirme** düğmesi <xref:System.Windows.Forms.Control.Click> olay işleyicisi çağrılarını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi bir <xref:System.ComponentModel.BackgroundWorker> karşıdan yükleme işlemini başlatmak için bileşen. Düğme karşıdan yükleme süresi boyunca devre dışı ve indirme işlemi tamamlandıktan sonra etkinleştirilir. A <xref:System.Windows.Forms.MessageBox> dosyanın içeriğini görüntüler.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Dosya indiriliyor**  
  
 Dosya indirildiğinde <xref:System.ComponentModel.BackgroundWorker> çalıştığı bileşenin iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Kodunuzu çağırdığında, bu iş parçacığı başlattığını <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yöntemi.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Bir BackgroundWorker tamamlanması bekleniyor**  
  
 `downloadButton_Click` Olay işleyicisi için beklenecek nasıl gösterir bir <xref:System.ComponentModel.BackgroundWorker> , zaman uyumsuz bir görevi tamamlamak için bileşen.  
  
 Yalnızca uygulama olaylara yanıt vermek istediğiniz ve arka plan iş parçacığı tamamlanmasını beklerken ana iş parçacığı herhangi bir iş yapmak istiyor musunuz, yalnızca işleyici çıkın.  
  
 Ana iş parçacığında iş yapmaya devam etmesini istiyorsanız, kullanın <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> belirlemek için özellik isteyip <xref:System.ComponentModel.BackgroundWorker> iş parçacığı hala çalışıyor. İndirme işlerken örnek bir ilerleme çubuğu güncelleştirilir. Çağırdığınızdan emin olun <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> UI esnek tutmak için yöntemi.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Sonuçları görüntüleme**  
  
 `backgroundWorker1_RunWorkerCompleted` Yöntemi tanıtıcıları <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay ve arka plan işlemi tamamlandığında çağırılır. Bu yöntem ilk denetler <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliği. Varsa <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> olduğu `null`, bu yöntem, dosyanın içeriğini görüntüler. Ardından indirme başladığında devre dışı bırakıldı, Yükle düğmesini etkinleştirir ve ilerleme çubuğu sıfırlar.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- System.Drawing System.Windows.Forms ve System.Xml derlemesine ilişkin başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Her zaman denetleyin <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> özelliğinde, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> erişmeye çalışmadan önce olay işleyicisi <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> özelliği veya tarafından etkilenmiş herhangi bir nesne <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
