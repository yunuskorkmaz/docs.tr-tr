---
title: 'Nasıl Yapılır: İşlemi Arka Planda Çalıştırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d17b2b982def283021bbd5d0ba7ab1e40ecf4e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-run-an-operation-in-the-background"></a>Nasıl Yapılır: İşlemi Arka Planda Çalıştırma
Tamamlanması uzun zaman alacağı işleme sahip ve kullanıcı arabiriminde gecikmelere neden istemediğiniz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıf.  
  
 Aşağıdaki kod örneğinde, uzun süren işlem arka planda çalışan gösterilmektedir. Formun **Başlat** ve **iptal** düğmeler. Tıklatın **Başlat** zaman uyumsuz bir işlem çalıştırmak için düğmesi. Tıklatın **iptal** çalışan zaman uyumsuz işlemi durdurmak için düğmesi. Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.  
  
 Bu görev için kapsamlı destek [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Ayrıca bkz. [izlenecek yol: bir işlemi arka planda çalışan](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [BackgroundWorker Bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
