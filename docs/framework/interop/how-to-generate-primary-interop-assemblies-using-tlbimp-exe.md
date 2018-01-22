---
title: "Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dfbf3c2282e60ec45cb136f52fb115a8d769678
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma
Birincil birlikte çalışma derlemesi oluşturmak için iki yolu vardır:  
  
-   Kullanarak [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
     Birincil birlikte çalışma derlemeleri üretmek için en kolay yolu kullanmaktır [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe aşağıdaki güvenlik önlemleri sağlar:  
  
    -   Tüm iç içe geçmiş tür kitaplığı başvuruları yeni birlikte çalışma derlemeleri oluşturmadan önce diğer kayıtlı birincil birlikte çalışma derlemeleri denetler.  
  
    -   Kapsayıcı ya da birincil birlikte çalışma derlemesi güçlü bir ad vermek için dosya adı belirtmezseniz, birincil birlikte çalışma derlemesi yaymak üzere başarısız olur.  
  
    -   Birincil birlikte çalışma derlemesi bağımlı derlemeleri başvurular atlarsanız yaymak üzere başarısız olur.  
  
    -   Birincil birlikte çalışma derlemeleri olmayan bağımlı derlemeleri başvurular eklerseniz, birincil birlikte çalışma derlemesi yaymak üzere başarısız olur.  
  
-   Birincil birlikte çalışma derlemeleri ile ortak dil belirtimi (CLS), C# gibi uyumlu bir dil kullanarak kaynak kodunda el ile oluşturma. Bu yaklaşım, bir tür kitaplığı kullanılamıyor yararlıdır.  
  
 Derlemeyi tanımlayıcı adla imzalamak için şifreleme anahtar çiftinin olması gerekir. Ayrıntılar için bkz [bir anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Tlbimp.exe kullanarak birincil birlikte çalışma derlemesi oluşturmak için  
  
1.  Komut isteminde, şunları yazın:  
  
     **Tlbimp** *tlbfile***/birincil/keyfile:** *filename* **/out:** *assemblyname*   
  
     Bu komutta *tlbfile* COM tür kitaplığı içeren bir dosya *filename* kapsayıcı veya anahtar çiftini içeren dosya adıdır ve *assemblyname* olduğu tanımlayıcı ad ile imzalamak için derleme adı.  
  
 Birincil birlikte çalışma derlemeleri yalnızca diğer birincil birlikte çalışma derlemeleri başvuruda bulunabilir. Derlemenizi bir üçüncü taraf COM tür kitaplığından türleri başvuruyorsa, birincil birlikte çalışma derlemenizi oluşturmadan önce birincil birlikte çalışma derlemesi yayımcıdan edinmeniz gerekir. Yayımcı varsa, başvuru birincil birlikte çalışma derlemesi oluşturmadan birincil birlikte çalışma için bir derleme bağımlı tür kitaplığı oluşturmanız gerekir.  
  
 Bağımlı bir birincil birlikte çalışma derlemesi özgün tür kitaplığı farklı bir sürüm numarası geçerli dizinde yüklendiğinde bulunabilirlik değil. Windows Kayıt Defteri'nde bağımlı birincil birlikte çalışma derlemesini kaydetme veya kullanmak **/reference** seçeneği Tlbimp.exe bağımlı DLL bulduğundan emin olun.  
  
 Tür kitaplığı birden fazla sürümünü de kayabilir. Yönergeler için bkz: [nasıl yapılır: kaydırma birden çok sürümleri, tür kitaplıklarının](http://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek COM tür kitaplığı içeri aktarır `LibUtil.tlb` ve derleme imzalar `LibUtil.dll` anahtar dosyası kullanarak tanımlayıcı bir ad ile `CompanyA.snk`. Belirli bir ad alanı adı kaldırarak bu örnek varsayılan ad alanı üretir `LibUtil`.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 Daha açıklayıcı bir ad için (kullanarak *SatıcıAdı*. *LibraryName* kılavuz adlandırma), aşağıdaki örnekte varsayılan derleme dosya adı ve ad alanı adı geçersiz kılar.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 Aşağıdaki örnek alır `MyLib.tlb`, hangi başvuruları `CompanyA.LibUtil.dll`, ve derleme imzalar `CompanyB.MyLib.dll` anahtar dosyası kullanarak tanımlayıcı bir ad ile `CompanyB.snk`. Ad alanı `CompanyB.MyLib`, varsayılan ad alanı adı geçersiz kılar.  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Birincil Birlikte Çalışma Bütünleştirilmiş Kodlarını Kaydetme](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
