---
title: ".NET Framework'te Güvenlik Değişiklikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: "52"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0777b2566337427abd116bb3584bc19e67d34803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework'te Güvenlik Değişiklikleri
Güvenlik için en önemli bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] güçlü adlandırma içinde değil. Bkz: [Gelişmiş tanımlayıcı adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md) bu değişikliklerin bir açıklaması için.  
  
 .NET Framework, yönetilen uygulamaları için iki katmanlı güvenlik modeli sağlar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır. Bu kapsayıcıda yönetilen uygulamaların tam olarak güvenilmeyen çalıştırın. Kod erişim güvenliği (CAS) açısından, hiçbir şey yoktur Geliştirici ayrıcalık yükseltme yapabilirsiniz. Windows tarafından verilen izinler hakkında daha fazla bilgi için bkz: [uygulama yeteneği bildirimleri (Windows mağazası uygulamaları)](http://go.microsoft.com/fwlink/?LinkId=230436) Windows geliştirme Merkezi'ndeki. Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama, bkz: [C# veya Visual Basic kullanarak ilk Windows mağazası uygulamanızı oluşturma](http://go.microsoft.com/fwlink/?LinkId=230461).
