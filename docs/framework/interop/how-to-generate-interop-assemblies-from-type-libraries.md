---
title: 'Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcdff732afce90f725f4730f0054296e389ada1b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051794"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma
[Tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) , com tür kitaplığı 'nda bulunan coclass 'ları ve arabirimleri meta verilere dönüştüren bir komut satırı aracıdır. Bu araç otomatik olarak tür bilgileri için birlikte çalışma derlemesi ve ad alanı oluşturur. Bir sınıfın meta verileri kullanılabilir olduktan sonra, yönetilen istemciler COM türünde örnekler oluşturabilir ve kendi yöntemlerini, tıpkı bir .NET örneğinde olduğu gibi çağırabilir. Tlbimp. exe bir tür kitaplığının tamamını aynı anda meta verilere dönüştürür ve tür kitaplığında tanımlanan türlerin bir alt kümesi için tür bilgisi üretmez.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Bir tür kitaplığından birlikte çalışma derlemesi oluşturmak için  
  
1. Aşağıdaki komutu kullanın:  
  
     **Tlbimp** *tür-kitaplık-dosya* \<>  
  
     **/Out:** anahtarını eklemek, krelib. dll gibi değiştirilmiş bir ada sahip bir birlikte çalışma derlemesi oluşturur. Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL 'sinden ayırt etmenize yardımcı olabilir ve yinelenen adlara sahip olmadan oluşabilecek sorunları önleyebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, `Loanlib` ad alanındaki krelib. dll derlemesini üretir.  
  
```  
tlbimp Loanlib.tlb  
```  
  
 Aşağıdaki komut, değiştirilmiş bir ada (Krelib. dll) sahip bir birlikte çalışma derlemesi üretir.  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](importing-a-type-library-as-an-assembly.md)
- [COM Bileşenlerini .NET Framework'te Gösterme](exposing-com-components.md)
