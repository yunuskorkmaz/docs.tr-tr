---
title: Şifreleme Düzeni Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1635276465dd58028c8a5e4b7e69a307664a4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580763"
---
# <a name="creating-a-cryptographic-scheme"></a>Şifreleme Düzeni Oluşturma
.NET Framework şifreleme bileşenlerinin şifrelemek ve verilerin şifresini çözmek için farklı düzenleri oluşturmak için birleştirilebilir.  
  
 Şifreleme ve verilerin şifresini çözmek için basit bir şifreleme şeması aşağıdakileri belirtebilir:  
  
1.  Her taraf ortak/özel anahtar çifti oluşturur.  
  
2.  Tarafların sitelerin genel anahtarlarını exchange.  
  
3.  Her taraf TripleDES şifreleme için gizli bir anahtar oluşturur örneğin ve diğer kişilerin ortak anahtar kullanarak yeni oluşturulan anahtarı şifreler.  
  
4.  Her taraf diğer verileri gönderir ve diğer kişilerin gizli anahtarı yeni gizli bir anahtar oluşturmak için kendi belirli bir sıra ile birleştirir.  
  
5.  Taraflar ardından simetrik şifreleme kullanarak bir konuşma başlatın.  
  
 Şifreleme düzeni oluşturma, karmaşık bir görev değil. Şifreleme kullanma hakkında daha fazla bilgi için Platform SDK belgelerine şifreleme konusuna bakın http://msdn.microsoft.com/library.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
