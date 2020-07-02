---
title: 'Nasıl Yapılır: İşlemi Arka Planda Çalıştırma'
description: Arka planda zaman alan Windows Forms işlemi çalıştırmak için BackgroundWorker sınıfını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621580"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Nasıl Yapılır: İşlemi Arka Planda Çalıştırma
Tamamlanması uzun süren bir işleme sahipseniz ve Kullanıcı arabiriminizdeki gecikmelere yol açmak istemiyorsanız, <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıfını kullanabilirsiniz.  
  
 Aşağıdaki kod örneği, arka planda zaman alan bir işlemin nasıl çalıştırılacağını gösterir. Form **Start** ve **Cancel** düğmelerine sahiptir. Zaman uyumsuz bir işlem çalıştırmak için **Başlat** düğmesine tıklayın. Çalışan bir zaman uyumsuz işlemi durdurmak için **iptal** düğmesine tıklayın. Her işlemin sonucu bir içinde görüntülenir <xref:System.Windows.Forms.MessageBox> .  
  
 Visual Studio 'da bu görev için kapsamlı destek vardır.  
  
 Ayrıca bkz. [Izlenecek yol: arka planda Işlem çalıştırma](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [BackgroundWorker Bileşeni](backgroundworker-component.md)
