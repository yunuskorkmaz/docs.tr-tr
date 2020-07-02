---
title: 'Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma'
description: Windows SDK tarafından sunulan tür kitaplığı alma programı (Tlbimp.exe) kullanarak birincil birlikte çalışma derlemeleri oluşturmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: 779b4863b6f1513f3566d4ab31660d88cda1039b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619136"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Nasıl yapılır: Tlbimp.exe Kullanarak Birincil Birlikte Çalışma Derlemeleri Oluşturma

Birincil birlikte çalışma derlemesi oluşturmak için iki yol vardır:

- Windows SDK tarafından sunulan [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) kullanılıyor.

  Birincil birlikte çalışma derlemelerini oluşturmanın en kolay yolu [Tlbimp.exe (tür kitaplığı alma programı)](../tools/tlbimp-exe-type-library-importer.md)kullanmaktır. Tlbimp.exe aşağıdaki korumaları sağlar:

  - Tüm iç içe geçmiş tür kitaplığı başvuruları için yeni birlikte çalışma derlemeleri oluşturmadan önce diğer kayıtlı birincil birlikte çalışma derlemelerini denetler.

  - Birincil birlikte çalışma derlemesine tanımlayıcı bir ad vermek için kapsayıcı veya dosya adı belirtmezseniz, birincil birlikte çalışma derlemesini yayma başarısız olur.

  - Bağımlı derlemelere yönelik başvuruları atlarsanız, birincil birlikte çalışma derlemesi yayılamıyor.

  - Birincil birlikte çalışma derlemeleri olmayan bağımlı derlemelere başvurular eklerseniz, birincil birlikte çalışma derlemesi yayılamıyor.

- C# gibi ortak dil belirtimi (CLS) ile uyumlu bir dil kullanarak kaynak kodunda el ile birincil birlikte çalışma derlemeleri oluşturma. Bu yaklaşım, bir tür kitaplığı kullanılamadığında yararlıdır.

Derlemeyi güçlü bir adla imzalamak için bir şifreleme anahtarı çiftiniz olması gerekir. Ayrıntılar için bkz. [anahtar çifti oluşturma](../../standard/assembly/create-public-private-key-pair.md).

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Tlbimp.exe kullanarak birincil birlikte çalışma derlemesi oluşturmak için

1. Komut istemine şunları yazın:

    **Tlbimp** *tlbdosya*  **/birincil/anahtar adı:** *filename* **/Out:** *AssemblyName*

    Bu komutta, *tlbdosya* com tür kitaplığını içeren dosyadır, *filename* anahtar çiftini içeren kapsayıcının veya dosyanın adı ve *AssemblyName* ise tanımlayıcı bir adla imzalanacak derlemenin adıdır.

Birincil birlikte çalışma derlemeleri yalnızca diğer birincil birlikte çalışma derlemelerine başvurabilir. Derlemeniz bir üçüncü taraf COM tür kitaplığından türlere başvuruyorsa, birincil birlikte çalışma derlemenizi oluşturabilmeniz için önce yayımcıdan bir birincil birlikte çalışma derlemesi edinmeniz gerekir. Yayımcı kullanıyorsanız, başvuran birincil birlikte çalışma derlemesini oluşturmadan önce bağımlı tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturmanız gerekir.

Özgün tür kitaplığından farklı bir sürüm numarasına sahip bağımlı bir birincil birlikte çalışma derlemesi, geçerli dizine yüklendiğinde keşfedilemez. Bağımlı birincil birlikte çalışma derlemesini Windows kayıt defterine kaydetmeniz veya Tlbimp.exe bağımlı DLL 'yi bulduğundan emin olmak için **/Reference** seçeneğini kullanmanız gerekir.

Ayrıca, bir tür kitaplığının birden çok sürümünü de kaydırabilirsiniz. Yönergeler için bkz. [nasıl yapılır: tür kitaplıklarının birden çok sürümünü sarın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).

## <a name="example"></a>Örnek

Aşağıdaki örnek, COM tür kitaplığını içeri aktarır `LibUtil.tlb` ve `LibUtil.dll` anahtar dosyasını kullanarak derlemeyi tanımlayıcı bir adla imzalar `CompanyA.snk` . Bu örnek, belirli bir ad alanı adını atlayarak varsayılan ad alanını üretir `LibUtil` .

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

Daha açıklayıcı bir ad ( *VendorName*kullanarak).* LibraryName* adlandırma Kılavuzu) aşağıdaki örnek, varsayılan derleme dosya adı ve ad alanı adını geçersiz kılar.

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

Aşağıdaki örnek içeri aktarır `MyLib.tlb` `CompanyA.LibUtil.dll` ve `CompanyB.MyLib.dll` anahtar dosyasını kullanarak derlemeyi tanımlayıcı bir adla imzalar `CompanyB.snk` . Ad alanı, `CompanyB.MyLib` varsayılan ad alanı adını geçersiz kılar.

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Birincil Birlikte Çalışma Derlemelerini Kaydetme](how-to-register-primary-interop-assemblies.md)
