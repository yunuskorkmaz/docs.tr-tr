---
title: 'Nasıl yapılır: Arka Planda İşlem Çalıştırma'
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
ms.openlocfilehash: 77f75a7eb1d7cc536df7110ef55727fbdf789f23
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591605"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Nasıl yapılır: Arka Planda İşlem Çalıştırma
Sahip olduğunuz işleminin tamamlanması uzun sürer ve kullanıcı arabiriminizde gecikmelere neden istiyor musunuz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> sınıfı, başka bir iş parçacığı üzerinde işlemi çalıştıramadı.  
  
 Aşağıdaki kod örneği, zaman alıcı bir işlem arka planda çalıştırılacak gösterilmektedir. Formundadır **Başlat** ve **iptal** düğmeleri. Tıklayın **Başlat** zaman uyumsuz bir işlemi çalıştırmak için düğme. Tıklayın **iptal** bir çalıştırma zaman uyumsuz işlemi durdurmak için düğmeye. Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.  
  
 Visual Studio'da bu görevi için kapsamlı desteği yoktur.  
  
 Ayrıca bkz: [izlenecek yol: Arka planda işlem çalıştırma](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [BackgroundWorker Bileşeni](backgroundworker-component.md)
