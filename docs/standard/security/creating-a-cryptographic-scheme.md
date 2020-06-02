---
title: Şifreleme Düzeni Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
ms.openlocfilehash: 1478873c1c2dc73ca31c9078e39a3902966bf674
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288426"
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

- [Şifreleme Hizmetleri](cryptographic-services.md)
