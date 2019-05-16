---
title: .NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 76c953941d2b8e7af5e4894fd1c521d62e64860f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642122"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)

COM nesneleri ve .NET Framework nesneleri aynı uygulamada kullanmak istediğinizde, nesneleri bellekte nasıl mevcut farklar adresi gerekir. .NET Framework nesnesi yönetilen bellekte bulunur; ortak dil çalışma zamanı tarafından denetlenen bellek — ve gerektiğinde çalışma zamanı tarafından taşınmış olabilir. Bir COM nesnesi yönetilmeyen bellekte bulunan ve başka bir bellek konumuna taşımak için beklenmiyor. Visual Studio ve .NET Framework, bu yönetilen ve yönetilmeyen bileşenler etkileşimi denetlemek için araçlar sağlar. Yönetilen kodu hakkında daha fazla bilgi için bkz. [ortak dil çalışma zamanı](../../../standard/clr.md).

.NET uygulamalarında COM nesneleri kullanmanın yanı sıra, ayrıca Visual Basic nesneleri, com ile yönetilmeyen koddan erişilebilir geliştirmek için kullanmak istediğiniz

Bu sayfadaki bağlantılar, COM ve .NET Framework nesneleri arasındaki etkileşimleri hakkında ayrıntılar sağlar.

## <a name="related-sections"></a>İlgili bölümler

| | |
|---------|---------|
| [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md) | Visual Basic'te COM nesneleri, ActiveX denetimleri, Win32 DLL'leri, yönetilen nesneleri ve COM nesneleri devralma dahil olmak üzere, COM birlikte çalışabilirlik kapsayan konulara bağlantılar sağlar. |
| [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md) | Kısaca, yönetilen ve yönetilmeyen kod arasındaki etkileşimi sorunlardan bazılarını açıklar ve daha fazla araştırma için bağlantılar sağlar. |
| [COM Sarmalayıcıları](../../../framework/interop/com-wrappers.md) | COM yöntemleri çağırmak yönetilen koda izin ver, çalışma zamanı aranabilir sarmalayıcılarını ve COM istemcilerinin .NET nesnesi yöntemlerini çağırmaya izin COM aranabilir sarmalayıcılarını ele alır. |
| [Gelişmiş COM birlikte çalışabilirliği](../../../framework/interop/index.md) | COM birlikte çalışabilirlik sarmalayıcılar, özel durumlar, devralma, iş parçacığı oluşturma, olayları, dönüştürme ve hazırlama göre kapsayan konulara bağlantılar sağlar. |
| [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Aracın, bir ortak dil çalışma zamanı derlemesi içindeki eşdeğer tanımlara bir COM tür kitaplığı içinde bulunan tür tanımlarını dönüştürme için kullanabileceğiniz anlatılmaktadır. |
