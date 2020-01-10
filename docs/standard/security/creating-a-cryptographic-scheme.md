---
title: Şifreleme Düzeni Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 00fff5f346633a9682d75cf6a3be7e8e7d5db7e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706298"
---
# <a name="creating-a-cryptographic-scheme"></a>Şifreleme Düzeni Oluşturma
.NET Framework şifreleme bileşenleri, verileri şifrelemek ve şifrelerini çözmek için farklı şemalar oluşturmak üzere birleştirilebilir.  
  
 Verileri şifrelemek ve şifrelerini çözmek için basit bir şifreleme şeması aşağıdaki adımları belirtebilir:  
  
1. Her taraf ortak/özel anahtar çifti oluşturur.  
  
2. Taraflar ortak anahtarlarını değiş tokuş altına alırlar.  
  
3. Her bir taraf, üç aylık şifreleme için gizli bir anahtar oluşturur, örneğin, diğer ortak anahtarını kullanarak yeni oluşturulan anahtarı şifreler.  
  
4. Her bir taraf, verileri birbirlerine gönderir ve yeni bir gizli anahtar oluşturmak için kendi gizli anahtarını belirli bir sırada kendi kendine birleştirir.  
  
5. Taraflar daha sonra simetrik şifrelemeyi kullanarak bir konuşma başlatır.  
  
 Şifreleme düzeni oluşturmak, önemsiz bir görev değildir.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
