---
title: "Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf56d33a791dd91614d5ae37e3568ef660696af7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Nasıl yapılır: Tür Kitaplıklarından Birlikte Çalışma Derlemeleri Oluşturma
[Tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) meta veriler için bir COM türü kitaplığında bulunan arabirimleri ve coclass'ları dönüştüren bir komut satırı aracıdır. Bu araç birlikte çalışma derlemesi ve ad alanı türü bilgileri için otomatik olarak oluşturur. Meta veri sınıfının kullanılabilir olduktan sonra yönetilen istemciler COM türünün örneklerini oluşturmak ve yalnızca bir .NET örneği gibi kendi yöntemlerini çağırın. Tlbimp.exe tüm tür kitaplığı meta verileri aynı anda dönüştürür ve bir tür kitaplığı'nda tanımlanan türlerden bir alt tür bilgileri oluşturulamıyor.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Birlikte çalışma bütünleştirilmiş bir tür kitaplığından oluşturmak için  
  
1.  Aşağıdaki komutu kullanın:  
  
     **Tlbimp** \< *türü kitaplık dosyası*>  
  
     Ekleme **/out:** anahtar LOANLib.dll gibi değiştirilmiş bir ad ile birlikte çalışma derleme üretir. Birlikte çalışma derleme adının değiştirilmesi, özgün COM DLL'den ayırt etmek ve yinelenen adları olan ortaya çıkabilecek sorunları önlemek yardımcı olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu Loanlib.dll derlemede üreten `Loanlib` ad alanı.  
  
```  
tlbimp Loanlib.dll  
```  
  
 Aşağıdaki komutu değiştirilmiş bir ad (LOANLib.dll) ile birlikte çalışma derleme üretir.  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür kitaplığını derleme olarak içeri aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [COM bileşenlerini .NET Framework'te gösterme](../../../docs/framework/interop/exposing-com-components.md)
