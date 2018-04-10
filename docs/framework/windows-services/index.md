---
title: Windows Hizmet Uygulamaları Geliştirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
caps.latest.revision: 18
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 325e43f4b1734bc6ab8753285e5069f36b0fda51
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="developing-windows-service-applications"></a>Windows Hizmet Uygulamaları Geliştirme
Microsoft kullanılarak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] veya Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, kolayca oluşturabileceğiniz Hizmetleri hizmeti olarak yüklenen bir uygulama oluşturarak. Bu tür bir uygulama bir Windows hizmeti adı verilir. Framework özelliklerle hizmetleri oluşturmak, bunları yüklemeniz ve Başlat, durdurabilir ve davranışlarını denetleyebilirsiniz.  
  
> [!WARNING]
>  Windows hizmet şablonu C++ için Visual Studio 2010'da dahil edilmedi. Bir Windows hizmeti oluşturmak için Visual C# veya Visual Basic, gerekirse mevcut C++ kodu ile birlikte çalışmak, yönetilen kodda bir hizmeti oluşturabilir veya kullanarak bir Windows hizmeti yerel C++'da oluşturabilirsiniz [ATL Proje Sihirbazı](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Hizmeti Uygulamalarına Giriş](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Bir hizmet ve hizmet uygulamalarının diğer ortak proje türlerinden farklılıklar ömrü Windows hizmet uygulamaları, genel bir bakış sağlar.  
  
 [İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Hizmet oluşturma örneğidir [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ve Visual C#.  
  
 [Hizmet Uygulaması Programlama Mimarisi](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Hizmet programlamada kullanılan dil öğeleri açıklanır.  
  
 [Nasıl Yapılır: Windows Hizmetleri Oluşturma](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Oluşturma ve Windows hizmeti proje şablonunu kullanarak Windows Hizmetleri yapılandırma sürecini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 <xref:System.ServiceProcess.ServiceBase>  
 En önemli özelliklerini açıklayan <xref:System.ServiceProcess.ServiceBase> hizmetleri oluşturmak için kullanılan sınıf.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Özelliklerini açıklayan <xref:System.ServiceProcess.ServiceProcessInstaller> ile birlikte kullanılan sınıf <xref:System.ServiceProcess.ServiceInstaller> yüklemek ve hizmetlerinizi kaldırmak için sınıf.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Özelliklerini açıklayan <xref:System.ServiceProcess.ServiceInstaller> ile birlikte kullanılan sınıf <xref:System.ServiceProcess.ServiceProcessInstaller> yükleyip hizmetinizi kaldırmak için sınıf.  
  
 [Şablonlardan NIB oluşturma projeleri](http://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Projeleri açıklar ve bunlar arasında seçim yapma Bu bölümde kullanılan türleri.
