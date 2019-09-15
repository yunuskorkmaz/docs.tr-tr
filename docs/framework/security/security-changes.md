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
ms.openlocfilehash: bfc48d4fed127b288353f0295f2de1ca33e0a8fe
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971205"
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework'te Güvenlik Değişiklikleri
.NET Framework 4,5 ' de güvenlikle olan en önemli değişiklik, tanımlayıcı adlandırmada. Bu değişikliklerin bir açıklaması için bkz. [Gelişmiş tanımlayıcı adlandırma](../../standard/assembly/enhanced-strong-naming.md) .  
  
 .NET Framework yönetilen uygulamalar için iki katmanlı bir güvenlik modeli sağlar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları, kaynaklara erişimi sınırlayan bir Windows güvenlik kapsayıcısında çalışır. Bu kapsayıcı içinde yönetilen uygulamalar tam olarak güvenilir çalışır. Bir kod erişimi güvenliği (CAS) perspektifinden, bir geliştiricinin ayrıcalıkları yükseltmek için yapabileceği bir şey yoktur. Windows tarafından verilen ayrıcalıklar hakkında daha fazla bilgi için, bkz. Windows Geliştirme Merkezi 'nde [uygulama yetenek bildirimleri (Windows Mağazası uygulamaları)](https://go.microsoft.com/fwlink/?LinkId=230436) . [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Uygulama oluşturma hakkında daha fazla bilgi için, bkz. [veya Visual Basic kullanarak C# ilk Windows mağazası uygulamanızı oluşturma](https://go.microsoft.com/fwlink/?LinkId=230461).
