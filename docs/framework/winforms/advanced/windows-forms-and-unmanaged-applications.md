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
ms.openlocfilehash: f54f039fd3477c380a2236a93ad8d80b4f7153b2
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441820"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms ve Yönetilmeyen Uygulamalar
Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalar ile çalışabilirler. Aşağıdaki bölümlerde, Windows Forms uygulamalarının ve denetimlerinin destekleyen ve destekledikleri değil, senaryolar ve yapılandırmaları açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Yönetilmeyen uygulamalar ile çalışan Windows Forms denetimleri uygulayın ve nasıl kullanılacağı hakkında genel bilgiler sunar.  
  
 [Nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışma desteği](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Nasıl kullanılacağını gösteren bir kod örneği sunar <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönetilmeyen bir uygulamada bir Windows Form çalıştırmak için yöntemi.  
  
 [Nasıl yapılır: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışma desteği](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Bir Windows formunu kendi iş parçacığında çalıştırmak üzere nasıl oluşturulduğunu gösteren bir kod örneği sağlar.  
  
 Ayrıca bkz: [izlenecek yol: Her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
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
