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
ms.openlocfilehash: cc388d68e5314604d3c8e8991b7fa3c600a5d873
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116733"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma
[Tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) meta verileri için bir COM tür kitaplığında bulunan arabirimleri ve coclass'ları dönüştürür bir komut satırı aracıdır. Bu araç bir birlikte çalışma derlemesi ve tür bilgisi için ad alanı otomatik olarak oluşturur. Bir sınıfın meta verileri kullanıma sunulduktan sonra yönetilen istemcilerin COM tür örnekleri oluşturma ve bir .NET örneği sanki olarak kendi yöntemlerini çağırmaya. Tlbimp.exe tüm tür kitaplığında tek seferde meta verisine dönüştürür ve tür kitaplığında tanımlanan türlerin bir alt kümesi için tür bilgisi oluşturulamıyor.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Tür kitaplığından bir birlikte çalışma derlemesi oluşturmak için  
  
1.  Aşağıdaki komutu kullanın:  
  
     **Tlbimp** \< *tür kitaplığı dosyası*>  
  
     Ekleme **/out:** anahtar LOANLib.dll gibi değiştirilmiş bir ad ile birlikte çalışma derlemesi oluşturur. Birlikte çalışma bütünleştirilmiş kod adı değiştirme yinelenen adları, oluşabilecek sorunları önlemek ve özgün COM DLL dosyasından ayırt yardımcı olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu Loanlib.dll derlemesinde oluşturur `Loanlib` ad alanı.  
  
```  
tlbimp Loanlib.tlb  
```  
  
 Aşağıdaki komut değiştirilen bir ad (LOANLib.dll) ile birlikte çalışma derlemesi oluşturur.  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [COM Bileşenlerini .NET Framework'te Gösterme](../../../docs/framework/interop/exposing-com-components.md)
