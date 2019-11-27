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
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204500"
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework'te Güvenlik Değişiklikleri

.NET Framework 4,5 ' de güvenlikle olan en önemli değişiklik, tanımlayıcı adlandırmada. Bu değişikliklerin bir açıklaması için bkz. [Gelişmiş tanımlayıcı adlandırma](../../standard/assembly/enhanced-strong-naming.md) .  
  
.NET Framework yönetilen uygulamalar için iki katmanlı bir güvenlik modeli sağlar. Windows 8. x Mağazası uygulamaları, kaynaklara erişimi sınırlayan bir Windows Güvenlik kapsayıcısında çalışır. Bu kapsayıcı içinde yönetilen uygulamalar tam olarak güvenilir çalışır. Bir kod erişimi güvenliği (CAS) perspektifinden, bir geliştiricinin ayrıcalıkları yükseltmek için yapabileceği bir şey yoktur. Windows tarafından verilen ayrıcalıklar hakkında daha fazla bilgi için, bkz. Windows Geliştirme Merkezi 'nde [uygulama yetenek bildirimleri (Windows Mağazası uygulamaları)](https://go.microsoft.com/fwlink/?LinkId=230436) . Windows 8. x Mağazası uygulaması oluşturma hakkında daha fazla bilgi için, bkz. [veya Visual Basic kullanarak C# ilk Windows mağazası uygulamanızı oluşturma](https://go.microsoft.com/fwlink/?LinkId=230461).
