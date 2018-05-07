---
title: .NET Framework'te Güvenlik Değişiklikleri
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84e80b99ee6d872714180e73354d20770c21e144
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework'te Güvenlik Değişiklikleri
Güvenlik için en önemli bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] güçlü adlandırma içinde değil. Bkz: [Gelişmiş tanımlayıcı adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md) bu değişikliklerin bir açıklaması için.  
  
 .NET Framework, yönetilen uygulamaları için iki katmanlı güvenlik modeli sağlar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır. Bu kapsayıcıda yönetilen uygulamaların tam olarak güvenilmeyen çalıştırın. Kod erişim güvenliği (CAS) açısından, hiçbir şey yoktur Geliştirici ayrıcalık yükseltme yapabilirsiniz. Windows tarafından verilen izinler hakkında daha fazla bilgi için bkz: [uygulama yeteneği bildirimleri (Windows mağazası uygulamaları)](http://go.microsoft.com/fwlink/?LinkId=230436) Windows geliştirme Merkezi'ndeki. Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, bkz: [C# veya Visual Basic kullanarak ilk Windows mağazası uygulamanızı oluşturma](http://go.microsoft.com/fwlink/?LinkId=230461).
