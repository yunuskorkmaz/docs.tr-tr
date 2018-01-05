---
title: "Windows Forms ve Yönetilmeyen Uygulamalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2672e8f87b28e81a9aa233cbf0f1b2c24b2239c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms ve Yönetilmeyen Uygulamalar
Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalarla birlikte çalışabilirler. Aşağıdaki bölümlerde Windows Forms uygulamaları ve denetimleri destekleyen ve değil destekleyen senaryoları ve yapılandırmaları açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 Yönetilmeyen uygulamalarla çalışma Windows Forms denetimleri uygulayın ve nasıl kullanılacağı hakkında genel bilgiler sunar.  
  
 [Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 Nasıl kullanılacağını gösteren kod örneği sağlar <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönetilmeyen bir uygulamada bir Windows formunda çalıştırılacak yöntemi.  
  
 [Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Bir Windows formunu kendi iş parçacığında çalıştırmak üzere gösteren kod örneği sağlar.  
  
 Ayrıca bkz. [izlenecek yol: COM birlikte çalışma destekleme görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Windows Form için ayrı bir iş parçacığı oluşturmak için kullanılır.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Bir iş parçacığı için ileti döngüsü başlatır.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Bir form için yönetilmeyen bir uygulamadan çağrıları sıralar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 .NET Framework türleri yönetilmeyen uygulamalarda kullanma hakkında genel bilgiler sunar.
