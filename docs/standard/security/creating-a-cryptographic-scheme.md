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
ms.openlocfilehash: 51d07fadcf359c2b44f22ca9868d0f12e24b80c5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873131"
---
# <a name="creating-a-cryptographic-scheme"></a>Şifreleme Düzeni Oluşturma
.NET Framework şifreleme bileşenlerini şifrelemek ve verilerin şifresini çözmek için farklı düzenleri oluşturmak için birleştirilebilir.  
  
 Şifreleme ve verilerin şifresini çözmek için basit bir şifreleme düzeni aşağıdakileri belirtebilirsiniz:  
  
1.  Her iki taraf bir ortak/özel anahtar çifti oluşturur.  
  
2.  Taraflar, ortak anahtar değişimi.  
  
3.  Her iki taraf TripleDES şifreleme için gizli bir anahtar oluşturur ve diğer kişinin ortak anahtar kullanarak yeni oluşturulan anahtarı şifreler.  
  
4.  Her bir taraf, diğer veri gönderir ve yeni bir gizli anahtar oluşturmak için kendi belirli bir siparişi ile diğer tarafın gizli anahtar birleştirir.  
  
5.  Taraflar ardından simetrik şifreleme kullanarak bir konuşma başlatır.  
  
 Şifreleme düzeni oluşturma, basit bir görev değildir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
