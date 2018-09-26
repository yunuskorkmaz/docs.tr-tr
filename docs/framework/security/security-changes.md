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
ms.openlocfilehash: c62a469b3e31283e5790c747092a8fe504ef8c2a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200561"
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework'te Güvenlik Değişiklikleri
Güvenlik için en önemli bir değişiklik [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] güçlü adlandırma olduğu. Bkz: [Gelişmiş kesin adlandırma](../../../docs/framework/app-domains/enhanced-strong-naming.md) bu değişikliklerin bir açıklaması için.  
  
 .NET Framework yönetilen uygulamalar için iki katmanlı güvenlik modeli sağlar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır. Bu kapsayıcı içinde yönetilen uygulamaların tam olarak güvenilen çalıştırın. Bir kod erişimi güvenliği (CAS) açısından bakıldığında, hiçbir şey yoktur bir geliştirici ayrıcalıklarını yükseltme yapabilirsiniz. Windows tarafından verilen izinler hakkında daha fazla bilgi için bkz. [uygulama yeteneği bildirimleri (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) Windows geliştirme Merkezi'nde. Oluşturma hakkında daha fazla bilgi için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması, bakın [C# veya Visual Basic kullanarak ilk Windows Store uygulamasını oluşturma](https://go.microsoft.com/fwlink/?LinkId=230461).
