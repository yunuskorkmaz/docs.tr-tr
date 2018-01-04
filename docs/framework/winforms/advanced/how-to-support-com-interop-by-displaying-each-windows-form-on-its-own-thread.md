---
title: "Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60e52bc1486f74bdce44062a4ac861032b7b660c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme
Üzerinde formunu görüntüleyerek COM birlikte çalışma sorunları çözebilirsiniz bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanarak oluşturabilirsiniz ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir COM istemci uygulamasından doğru şekilde bir Windows Form çalışmasını sağlamak için bir Windows Forms ileti döngüsü formun çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
-   Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows formunu görüntüleme yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte'çalışma Destek](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin.  
  
 Bu özellik için kapsamlı destek [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
 Ayrıca bkz. [izlenecek yol: COM birlikte çalışma destekleme görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir ayrı bir iş parçacığı ve çağrı formu görüntülenecek gösterilmiştir <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> o iş parçacığı üzerinde bir Windows Forms ileti Pompalama başlatmak için yöntem. Bu yaklaşımı kullanmak için formun yapılan her çağrı yönetilmeyen uygulamasından kullanarak sıralamanız gerekir <xref:System.Windows.Forms.Control.Invoke%2A> yöntemi.  
  
 Bu yaklaşım, her bir form örneği kendi ileti döngüsü kullanarak kendi iş parçacığında çalıştırmasını gerektirir. İş parçacığı çalışan birden fazla ileti döngüsüne sahip olamaz. Bu nedenle, istemci uygulamanın ileti döngüsü değiştiremezsiniz. Ancak, değiştirebileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bileşeni için kendi ileti döngüsü kullanan yeni bir iş parçacığı başlatılamıyor.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Derleme `COMForm`, `Form1`, ve `FormManager` bir bütünleştirilmiş türleri olarak da adlandırılır `COMWinform.dll`. COM birlikte çalışma için derleme açıklanan yöntemlerden birini kullanarak kaydedin [COM için derlemeyi paketleme](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Artık derleme ve yönetilmeyen uygulamalar karşılık gelen alt türü kitaplığı (.tlb) dosyasında da kullanabilirsiniz. Örneğin, tür kitaplığı Visual Basic 6.0 yürütülebilir bir proje başvuru olarak kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [COM için Bütünleştirilmiş Kod Paketleme](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Bütünleştirilmiş Kodları COM ile Kaydetme](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
