---
title: "Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f01fc82be38f7c5acb02c28960785e97a782909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme
Üzerinde Windows formunu görüntüleyerek Bileşen Nesne Modeli (COM) birlikte çalışabilirlik sorunlarını çözebilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanılarak oluşturulan ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.  
  
 Doğru bir COM istemci uygulamasından çalışması bir form yapmak için bir Windows Forms ileti döngüsü çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
-   Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Windows Form; görüntülenecek yöntemi  
  
-   Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin. Daha fazla bilgi için bkz: [nasıl yapılır: Destek COM birlikte çalışma görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Yordam  
 Kullanarak <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemi, bir form görüntülemek için en kolay yolu olabilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] olduğundan, döngü ileti isteğe bağlı olarak tüm yaklaşımlardan, uygulamak için en az kod gerektirir.  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Yöntemi yönetilmeyen uygulamanın ileti döngüsü askıya alır ve formu olarak iletişim kutusu görüntüler. Konak uygulamanın ileti döngüsü askıya alındığından <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemi yeni bir oluşturur [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] formun iletileri işlemek için ileti döngüsü.  
  
 Kullanmanın olumsuz yanı <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemdir form kalıcı bir iletişim kutusu açılır. Windows formu açıkken bu davranış herhangi bir kullanıcı arabirimi (UI) çağıran uygulamada engeller. Kullanıcı formu çıktığında [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ileti döngüsü kapatır ve döngü başlatır yeniden çalıştırmayı önceki uygulamanın ileti.  
  
 Windows Forms içinde formu göstermek için bir yöntem olan bir sınıf kitaplığı oluşturmak ve COM birlikte çalışma için sınıf kitaplığı oluşturmak. Visual Basic 6.0 veya Microsoft Foundation sınıfları (MFC) bu DLL dosyasını kullanabilirsiniz ve bu ortamları birinden çağırabilirsiniz <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> formun görüntülenecek yöntemi.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>ShowDialog yöntemi ile bir windows formunu görüntüleyerek COM birlikte çalışma desteklemek için  
  
-   Tüm çağrıları Değiştir <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> çağrıları yöntemiyle <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönteminde, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bileşeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework bileşenlerini COM'da gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Nasıl yapılır: her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 [Windows Forms ve yönetilmeyen uygulamalar](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
