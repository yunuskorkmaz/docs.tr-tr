---
title: ".NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9347f7771e0e86f9a19cbec94ef59dcf1bdb250
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)
COM ve .NET Framework nesneleri aynı uygulamada kullanmak istediğinizde, nesnelerin nasıl bellekte mevcut farklar adresi gerekir. .NET Framework nesne yönetilen bellekte yer alan — ortak dil çalışma zamanı tarafından denetlenen bellek — ve çalışma zamanı tarafından gerektiği şekilde taşınmış olabilir. Bir COM nesnesi yönetilmeyen bellekte bulunur ve başka bir bellek konumuna taşımak için beklenmiyor. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] bu etkileşimini denetlemek için Araçlar yönetilen ve yönetilmeyen bileşenleri sağlar. Yönetilen kodu hakkında daha fazla bilgi için bkz: [ortak dil çalışma zamanı](../../../standard/clr.md).  
  
 COM nesneleri .NET uygulamalarında kullanmanın yanı sıra, aynı zamanda kullanmak isteyebilirsiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nesneleri COM yoluyla yönetilmeyen koddan erişilebilir geliştirmek için  
  
 Bu sayfadaki bağlantıları COM ve .NET Framework nesneleri arasındaki etkileşimleri hakkında ayrıntılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [COM birlikte çalışma](../../../visual-basic/programming-guide/com-interop/index.md)  
 Visual Basic'te COM nesneleri, ActiveX denetimleri, Win32 DLL'leri, yönetilen nesneleri ve COM nesnelerini devralma dahil olmak üzere, COM birlikte çalışabilirliği kapsayan konulara bağlantılar sağlar.  
  
 [COM birlikte çalışma sarmalayıcısı hatası](/cpp/misc/com-interop-wrapper-error)  
 Proje sistemi için belirli bir bileşene COM birlikte çalışabilirliği sarmalayıcı oluşturursanız sonuçları ve seçenekleri açıklanmaktadır.  
  
 [Yönetilmeyen kod ile birlikte çalışma](https://msdn.microsoft.com/library/sd10k43k)  
 Kısaca bazıları yönetilen ve yönetilmeyen kodu arasında etkileşim sorunlarına açıklar ve daha fazla olay incelemesi için bağlantılar sağlar.  
  
 [COM sarmalayıcıları](../../../framework/interop/com-wrappers.md)  
 COM yöntemleri çağırmak yönetilen kod izin verme, çalışma zamanı aranabilir sarmalayıcıları ve .NET nesne yöntemleri çağırmak COM istemcileri izin COM aranabilir sarmalayıcılar anlatılmaktadır.  
  
 [Gelişmiş COM birlikte çalışabilirliği](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 COM birlikte çalışabilirliği sarmalayıcıları, özel durumlar, devralma, iş parçacığı oluşturma, olaylar, dönüştürme ve hazırlama göre kapsayan konulara bağlantılar sağlar.  
  
 [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 Ortak dil çalışma zamanı derlemesi eşdeğer tanımlarında içine bir COM tür kitaplığı içinde bulunan tür tanımları dönüştürmek için kullanabileceğiniz aracı anlatılır.
