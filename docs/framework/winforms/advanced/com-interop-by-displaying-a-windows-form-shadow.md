---
title: 'Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
ms.openlocfilehash: 81220ad4c0bf00a38abfe7257d5fc61e92e8d885
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206453"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme
Şirket, Windows formunu görüntüleyerek Bileşen Nesne Modeli (COM) birlikte çalışabilirlik sorunları çözebilirsiniz bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kullanılarak oluşturulan ileti döngüsü <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> yöntemi.  
  
 Bir form düzgün bir COM istemci uygulamasından çalışması yapmak için bir Windows Forms ileti döngüsü üzerinde çalıştırmanız gerekir. Bunu yapmak için aşağıdaki yaklaşımlardan birini kullanın:  
  
-   Kullanım <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> ; Windows formu görüntülemek için yöntemi  
  
-   Her Windows formunu ayrı bir iş parçacığı üzerinde görüntüleyin. Daha fazla bilgi için [nasıl yapılır: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Yordam  
 Kullanarak <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemi, bir form görüntülemek için en kolay yolu olabilir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] olduğundan ileti döngüsü uygulamak için en az kod gerektirdiği yaklaşımlardan.  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> Yöntemi yönetilmeyen uygulamanın ileti döngüsü askıya alır ve bir iletişim kutusu olarak form görüntüler. Konak uygulamanın ileti döngüsü askıya alındığından <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemi yeni bir oluşturur [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] formun iletileri işlemek için ileti döngüsü.  
  
 Kullanılarak dezavantajı <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yöntemdir form kalıcı bir iletişim kutusu açılır. Windows formu açıkken bu davranış çağıran uygulamada herhangi bir kullanıcı arabirimi (UI) engeller. Kullanıcı formu çıktığında [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ileti döngüsü kapanır ve döngü başlatır yeniden çalıştırmayı önceki uygulamanın ileti.  
  
 Bir sınıf kitaplığı formu göstermek için bir yöntem olan Windows Formları oluşturabilir ve ardından COM birlikte çalışması için sınıf kitaplığı oluşturun. Bu DLL dosyasını Visual Basic 6.0 veya Microsoft Foundation Classes (MFC) kullanabilirsiniz ve bu ortamların birini çağırabilirsiniz <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> formu görüntülemek için yöntemi.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>ShowDialog yöntemi ile bir windows formunu görüntüleyerek COM birlikte çalışma desteklemek için  
  
-   Tüm çağrıları değiştirin <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> yöntemi çağrılarıyla <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönteminde, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bileşeni.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Bileşenlerini COM'da Gösterme](../../interop/exposing-dotnet-components-to-com.md)
- [Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
- [Windows Forms ve Yönetilmeyen Uygulamalar](windows-forms-and-unmanaged-applications.md)
