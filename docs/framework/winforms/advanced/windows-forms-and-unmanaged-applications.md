---
title: Yönetilmeyen uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746359"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms ve Yönetilmeyen Uygulamalar
Windows Forms uygulamalar ve denetimler, bazı uyarılarla yönetilmeyen uygulamalarla birlikte çalışabilir. Aşağıdaki bölümlerde, uygulamaları ve denetimleri Windows Forms uygulamalar ve denetimlerin desteklediği senaryolar ve Konfigürasyonlar açıklanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](windows-forms-and-unmanaged-applications-overview.md)  
 , Yönetilmeyen uygulamalarla çalışan Windows Forms denetimlerinin kullanımı ve uygulanması hakkında genel bilgiler sunar.  
  
 [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](com-interop-by-displaying-a-windows-form-shadow.md)  
 Yönetilmeyen bir uygulamada Windows formunu çalıştırmak için <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönteminin nasıl kullanılacağını gösteren bir kod örneği sağlar.  
  
 [Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Kendi iş parçacığında bir Windows formunun nasıl çalıştırılacağını gösteren bir kod örneği sağlar.  
  
 Ayrıca bkz. [Izlenecek yol: her Windows formunu kendi Iş parçacığında görüntüleyerek com birlikte çalışmasını destekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Bir Windows formu için ayrı bir iş parçacığı oluşturmak için kullanılır.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 İş parçacığı için bir ileti döngüsü başlatır.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Yönetilmeyen bir uygulamadan bir forma yapılan çağrı öğeleri.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../interop/exposing-dotnet-components-to-com.md)  
 Yönetilmeyen uygulamalarda .NET Framework türlerini kullanma hakkında genel bilgiler sunar.
