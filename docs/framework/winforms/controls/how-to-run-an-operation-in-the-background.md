---
title: 'Nasıl Yapılır: İşlemi Arka Planda Çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 7a2ce452a1e55d0b01245c4eb7f43056031b9e2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533919"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Nasıl Yapılır: İşlemi Arka Planda Çalıştırma
Tamamlanması uzun zaman alacağı işleme sahip ve kullanıcı arabiriminde gecikmelere neden istemediğiniz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıf.  
  
 Aşağıdaki kod örneğinde, uzun süren işlem arka planda çalışan gösterilmektedir. Formun **Başlat** ve **iptal** düğmeler. Tıklatın **Başlat** zaman uyumsuz bir işlem çalıştırmak için düğmesi. Tıklatın **iptal** çalışan zaman uyumsuz işlemi durdurmak için düğmesi. Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.  
  
 Visual Studio'da bu görev için kapsamlı destek yoktur.  
  
 Ayrıca bkz. [izlenecek yol: bir işlemi arka planda çalışan](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [BackgroundWorker Bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
