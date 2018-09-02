---
title: Windows Forms ve Yönetilmeyen Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: bc0c848d1c92871dacab93497c674645f3ac83fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463945"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms ve Yönetilmeyen Uygulamalar
Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalar ile çalışabilirler. Aşağıdaki bölümlerde, Windows Forms uygulamalarının ve denetimlerinin destekleyen ve destekledikleri değil, senaryolar ve yapılandırmaları açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Yönetilmeyen uygulamalar ile çalışan Windows Forms denetimleri uygulayın ve nasıl kullanılacağı hakkında genel bilgiler sunar.  
  
 [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Nasıl kullanılacağını gösteren bir kod örneği sunar <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönetilmeyen bir uygulamada bir Windows Form çalıştırmak için yöntemi.  
  
 [Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Bir Windows formunu kendi iş parçacığında çalıştırmak üzere nasıl oluşturulduğunu gösteren bir kod örneği sağlar.  
  
 Ayrıca bkz: [izlenecek yol: COM birlikte çalışabilirlik destekleyen görüntüleme her Windows formunu kendi kendi iş parçacığı üzerinde tarafından](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Windows Form için ayrı bir iş parçacığı oluşturmak için kullanılır.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Bir iş parçacığı için bir ileti döngüsü başlatır.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Bir form için yönetilmeyen bir uygulamadan çağrıları sürekliliğe devreder.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 Yönetilmeyen uygulamalarda .NET Framework türlerini kullanımı hakkında genel bilgi sunar.
