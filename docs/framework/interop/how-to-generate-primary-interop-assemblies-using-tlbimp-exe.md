---
title: 'Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839b0ed6f8e9868e1a3d8e19cc6e8a580313d160
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146438"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma
Birincil birlikte çalışma derlemesi oluşturmak için iki yolunuz vardır:  
  
-   Kullanarak [tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
     Birincil birlikte çalışma derlemeleri oluşturmak için en kolay yolu [Tlbimp.exe (tür kitaplığı içeri Aktarıcı)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe aşağıdaki güvenlik önlemleri sağlar:  
  
    -   Tüm iç içe geçmiş tür kitaplığı başvurularını için yeni birlikte çalışma derlemeleri oluşturmadan önce diğer kayıtlı birincil birlikte çalışma derlemelerini denetler.  
  
    -   Kapsayıcı ya da birincil birlikte çalışma derlemesini bir katı ad vermek için dosya adı belirtmezseniz, birincil birlikte çalışma derlemesi yaymak başarısız olur.  
  
    -   Bağımlı derlemelerin başvurularını atlarsanız, birincil birlikte çalışma derlemesi yaymak başarısız olur.  
  
    -   Birincil birlikte çalışma derlemelerini olmayan bağımlı derlemelerin başvurularını eklerseniz, birincil birlikte çalışma derlemesi yaymak başarısız olur.  
  
-   Kaynak kodunda el ile oluşturma gibi ortak dil belirtimi (CLS) ile uyumlu bir dil kullanarak birincil birlikte çalışma derlemelerini C#. Bu yaklaşım, bir tür kitaplığı kullanılamadığında yararlıdır.  
  
 Derlemeyi tanımlayıcı bir adla imzalamak için bir şifreleme anahtarı çiftiniz olması gerekir. Ayrıntılar için bkz [bir anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Tlbimp.exe kullanarak birincil birlikte çalışma derlemesi oluşturmak için  
  
1.  Komut isteminde, şunları yazın:  
  
     **Tlbimp** *tlbfile***/birincil/keyfile:** *filename* **/out:** *assemblyname*  
  
     Bu komutta *tlbfile* COM tür kitaplığı içeren bir dosya *filename* kapsayıcısı veya anahtar çiftini içeren dosyanın adı ve *assemblyname* olduğu tanımlayıcı ad ile işaretlenecek derlemenin adı.  
  
 Birincil birlikte çalışma derlemeleri, yalnızca diğer birincil birlikte çalışma derlemelerini başvurabilirsiniz. Derlemenizi üçüncü taraf COM tür kitaplığından türleri başvuruyorsa, birincil birlikte çalışma bütünleştirilmiş kodunuzda oluşturmadan önce bir birincil birlikte çalışma derlemesi yayımcıdan edinmeniz gerekir. Yayımcı ise başvuru birincil birlikte çalışma bütünleştirilmiş kodu oluşturuluyor önce birincil birlikte çalışma derlemesi bağımlı tür kitaplığı için oluşturmanız gerekir.  
  
 Bağımlı bir birincil birlikte çalışma derlemesi, özgün tür kitaplığına farklı bir sürüm numarası geçerli dizinde yüklendiğinde bulunabilirlik değil. Windows kayıt defterinde bağımlı birincil birlikte çalışma derlemesi veya kullanın **/reference** Tlbimp.exe bağımlı DLL bulur emin olmak için seçeneği.  
  
 Ayrıca, birden çok tür kitaplığı sürümünü sarabilirsiniz. Yönergeler için [nasıl yapılır: Birden çok tür kitaplığı sürümünü sarmalama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, COM tür kitaplığı içeri aktarır `LibUtil.tlb` ve derlemeyi imzalar `LibUtil.dll` anahtar dosyasını kullanarak bir katı adla `CompanyA.snk`. Bu örnek varsayılan ad üretir belirli ad alanı adı gt;(yok) `LibUtil`.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 Daha açıklayıcı bir ad için (kullanarak *SatıcıAdı*. *LibraryName* kılavuz adlandırma), aşağıdaki örnekte varsayılan derleme dosya adı ve ad alanı adını geçersiz kılar.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 Aşağıdaki örnek alır `MyLib.tlb`, hangi başvurular `CompanyA.LibUtil.dll`, ve derlemeyi imzalar `CompanyB.MyLib.dll` anahtar dosyasını kullanarak bir katı adla `CompanyB.snk`. Ad alanı `CompanyB.MyLib`, varsayılan ad alanı adını geçersiz kılar.  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
