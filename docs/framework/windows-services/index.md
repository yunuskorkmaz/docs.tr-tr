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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053551"
---
# <a name="develop-windows-service-apps"></a>Windows hizmeti uygulamaları geliştirme

Visual Studio veya .NET Framework SDK kullanarak, hizmet olarak yüklenen bir uygulama oluşturarak kolayca hizmet oluşturabilirsiniz. Bu tür bir uygulama Windows hizmeti olarak adlandırılır. Çerçeve özellikleri sayesinde, hizmetler oluşturabilir, bunları yükleyebilir ve davranışlarını başlatabilir, durdurabilir ve başka bir şekilde denetleyebilirsiniz.

> [!NOTE]
> Visual Studio 'da, Visual C# veya Visual Basic yönetilen kodda bir hizmet oluşturabilirsiniz. Bu, gerekirse mevcut C++ kodla birlikte çalışabilir. Veya, C++ [atl Proje Sihirbazı 'nı](/cpp/atl/reference/atl-project-wizard)kullanarak yerel olarak bir Windows hizmeti oluşturabilirsiniz.

## <a name="in-this-section"></a>Bu bölümde

[Windows Hizmeti Uygulamalarına Giriş](introduction-to-windows-service-applications.md)

Windows hizmet uygulamalarına genel bakış, bir hizmetin kullanım süresi ve hizmet uygulamalarının diğer ortak proje türlerinden farkı nasıl farklılık gösterir.

[İzlenecek yol: Bileşen tasarımcısında bir Windows hizmeti uygulaması oluşturma](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Visual Basic ve görselde C#bir hizmet oluşturma örneği sağlar.

[Hizmet Uygulaması Programlama Mimarisi](service-application-programming-architecture.md)

Hizmet programlamasında kullanılan dil öğelerini açıklar.

[Nasıl yapılır: Windows Hizmetleri oluşturma](how-to-create-windows-services.md)

Windows hizmeti proje şablonunu kullanarak Windows hizmetlerini oluşturma ve yapılandırma sürecini açıklar.

## <a name="related-sections"></a>İlgili bölümler

<xref:System.ServiceProcess.ServiceBase>- <xref:System.ServiceProcess.ServiceBase> Sınıfının hizmetleri oluşturmak için kullanılan ana özelliklerini açıklar.

<xref:System.ServiceProcess.ServiceProcessInstaller>-Hizmetlerinizi yüklemek ve kaldırmak için <xref:System.ServiceProcess.ServiceProcessInstaller> <xref:System.ServiceProcess.ServiceInstaller> sınıfıyla birlikte kullanılan sınıfının özelliklerini açıklar.

<xref:System.ServiceProcess.ServiceInstaller>-Hizmetinizi yüklemek ve kaldırmak için <xref:System.ServiceProcess.ServiceInstaller> <xref:System.ServiceProcess.ServiceProcessInstaller> sınıfıyla birlikte kullanılan sınıfının özelliklerini açıklar.

[Şablonlardan proje oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -bu bölümde kullanılan proje türlerini ve bunların arasından nasıl seçim yapılacağını açıklar.
