---
title: Windows Hizmet Uygulamaları Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71053551"
---
# <a name="develop-windows-service-apps"></a>Windows hizmet uygulamaları geliştirme

Visual Studio veya .NET Framework SDK'yı kullanarak, hizmet olarak yüklenmiş bir uygulama oluşturarak kolayca hizmet oluşturabilirsiniz. Bu tür bir uygulama Windows hizmeti olarak adlandırılır. Çerçeve özellikleriyle, hizmetleri oluşturabilir, yükleyebilir ve davranışlarını başlatabilir, durdurabilir ve başka bir şekilde denetleyebilirsiniz.

> [!NOTE]
> Visual Studio'da Visual C# veya Visual Basic'te yönetilen kodda, gerektiğinde varolan C++ koduyla birlikte çalışabilen bir hizmet oluşturabilirsiniz. Veya, [ATL Project Wizard'ı](/cpp/atl/reference/atl-project-wizard)kullanarak yerel C++'da bir Windows hizmeti oluşturabilirsiniz.

## <a name="in-this-section"></a>Bu bölümde

[Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)

Windows hizmet uygulamalarına genel bakış, bir hizmetin kullanım ömrü ve hizmet uygulamalarının diğer yaygın proje türlerinden nasıl farklı olduğu hakkında genel bir bakış sağlar.

[İzlenecek Yol: Bileşen Tasarımcısında Windows Hizmeti Uygulaması Oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Visual Basic ve Visual C#'da bir hizmet oluşturmaya bir örnek sağlar.

[Hizmet Uygulaması Programlama Mimarisi](service-application-programming-architecture.md)

Hizmet programlamada kullanılan dil öğelerini açıklar.

[Nasıl Yapılır: Windows Hizmetleri Oluşturma](how-to-create-windows-services.md)

Windows hizmeti proje şablonu kullanarak Windows hizmetleri oluşturma ve yapılandırma işlemini açıklar.

## <a name="related-sections"></a>İlgili bölümler

<xref:System.ServiceProcess.ServiceBase>- Hizmet oluşturmak için <xref:System.ServiceProcess.ServiceBase> kullanılan sınıfın temel özelliklerini açıklar.

<xref:System.ServiceProcess.ServiceProcessInstaller>- Hizmetlerinizi yüklemek <xref:System.ServiceProcess.ServiceProcessInstaller> ve kaldırmak için <xref:System.ServiceProcess.ServiceInstaller> sınıfla birlikte kullanılan sınıfın özelliklerini açıklar.

<xref:System.ServiceProcess.ServiceInstaller>- Hizmetinizi yüklemek <xref:System.ServiceProcess.ServiceInstaller> ve kaldırmak için <xref:System.ServiceProcess.ServiceProcessInstaller> sınıfla birlikte kullanılan sınıfın özelliklerini açıklar.

[Şablonlardan Projeler Oluştur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - Bu bölümde kullanılan proje türlerini ve aralarındanasıl seçim yapılacağını açıklar.
