---
title: 'Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: d0d8dfd4a19b31be790d2643847396d136098278
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085614"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme
Üzerinde formunu görüntüleyerek COM birlikte çalışabilirlik sorunları çözebilirsiniz bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanarak oluşturabileceğiniz ileti döngüsü, <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir COM istemci uygulamasından doğru şekilde bir Windows Form çalışmasını sağlamak için form üzerinde bir Windows Forms ileti döngüsü çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
-   Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows formu görüntülemek için yöntemi. Daha fazla bilgi için [nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte'çalışma desteği](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin.  
  
 Visual Studio'da bu özellik için kapsamlı desteği yoktur.  
  
 Ayrıca bkz: [izlenecek yol: COM birlikte çalışabilirlik destekleyen görüntüleme her Windows formunu kendi kendi iş parçacığı üzerinde tarafından](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir ayrı iş parçacığı ve çağrı formu görüntülemek gösterilmiştir <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> o iş parçacığı üzerinde bir Windows Forms ileti pompası başlatmak için yöntemi. Bu yaklaşımı kullanmak için form yönetilmeyen bir uygulamadan gelen çağrıları kullanarak sıralamanız gerekir <xref:System.Windows.Forms.Control.Invoke%2A> yöntemi.  
  
 Bu yaklaşım, formu her örneği, kendi ileti döngüsü kullanarak kendi iş parçacığında çalıştıran gerektirir. Çalışan iş parçacığı birden fazla ileti döngüsü sahip olamaz. Bu nedenle, istemci uygulamanın ileti döngüsü değiştiremezsiniz. Ancak, değiştirebileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kendi ileti döngüsü kullanan yeni bir iş parçacığı bileşeni.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Derleme `COMForm`, `Form1`, ve `FormManager` tür bir derleme olarak adlandırılan `COMWinform.dll`. COM birlikte çalışma bütünleştirilmiş kod içinde açıklanan yöntemlerden birini kullanarak kayıt [COM için derlemeyi paketleme](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Artık, derleme ve yönetilmeyen uygulamalarda karşılık gelen tür kitaplığını (.tlb) dosyasını da kullanabilirsiniz. Örneğin, bir Visual Basic 6.0 yürütülebilir projeyi başvuru olarak tür kitaplığını kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [COM için Bütünleştirilmiş Kod Paketleme](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Bütünleştirilmiş Kodları COM ile Kaydetme](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
