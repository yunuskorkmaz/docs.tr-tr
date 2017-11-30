---
title: "Şifreleme Düzeni Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e3c4a832f70fae7808bf71016cb9f6648332f01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-cryptographic-scheme"></a>Şifreleme Düzeni Oluşturma
.NET Framework şifreleme bileşenlerinin şifrelemek ve verilerin şifresini çözmek için farklı düzenleri oluşturmak için birleştirilebilir.  
  
 Şifreleme ve verilerin şifresini çözmek için basit bir şifreleme şeması aşağıdakileri belirtebilir:  
  
1.  Her taraf ortak/özel anahtar çifti oluşturur.  
  
2.  Tarafların sitelerin genel anahtarlarını exchange.  
  
3.  Her taraf TripleDES şifreleme için gizli bir anahtar oluşturur örneğin ve diğer kişilerin ortak anahtar kullanarak yeni oluşturulan anahtarı şifreler.  
  
4.  Her taraf diğer verileri gönderir ve diğer kişilerin gizli anahtarı yeni gizli bir anahtar oluşturmak için kendi belirli bir sıra ile birleştirir.  
  
5.  Taraflar ardından simetrik şifreleme kullanarak bir konuşma başlatın.  
  
 Şifreleme düzeni oluşturma, karmaşık bir görev değil. Şifreleme kullanma hakkında daha fazla bilgi için Platform SDK belgelerine http://msdn.microsoft.com/library şifreleme konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)
