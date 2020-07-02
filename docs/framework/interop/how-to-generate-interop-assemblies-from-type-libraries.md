---
title: 'Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma'
description: Tür kitaplıklarından birlikte çalışma derlemeleri oluşturun. Ortak sınıfları ve arabirimleri bir COM tür kitaplığından meta verilere dönüştürmek için tür kitaplığı alma programı (Tlbimp.exe) kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 6f54875d6aadb1da18cf25a1bec0a0e451f4a24c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619565"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma
[Tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) , com tür kitaplığı 'nda bulunan coclass 'ları ve arabirimlerin meta verilere dönüştürüldüğü bir komut satırı aracıdır. Bu araç otomatik olarak tür bilgileri için birlikte çalışma derlemesi ve ad alanı oluşturur. Bir sınıfın meta verileri kullanılabilir olduktan sonra, yönetilen istemciler COM türünde örnekler oluşturabilir ve kendi yöntemlerini, tıpkı bir .NET örneğinde olduğu gibi çağırabilir. Tlbimp.exe, tüm tür kitaplığını tek seferde meta verilere dönüştürür ve bir tür kitaplığında tanımlanan türlerin bir alt kümesi için tür bilgisi üretemiyor.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Bir tür kitaplığından birlikte çalışma derlemesi oluşturmak için  
  
1. Aşağıdaki komutu kullanın:  
  
     **Tlbimp**\<*type-library-file*>  
  
     **/Out:** anahtarını eklemek, LOANLib.dll gibi değiştirilmiş bir ada sahip bir birlikte çalışma derlemesi üretir. Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL 'sinden ayırt etmenize yardımcı olabilir ve yinelenen adlara sahip olmadan oluşabilecek sorunları önleyebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut ad alanında Loanlib.dll derlemesini üretir `Loanlib` .  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 Aşağıdaki komut, değiştirilmiş bir ada (LOANLib.dll) sahip bir birlikte çalışma derlemesi üretir.  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
