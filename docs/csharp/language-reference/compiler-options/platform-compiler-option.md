---
title: -platform (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: ae2305e0f5d3ca4de386d8e7933a1107450e0be4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341510"
---
# <a name="-platform-c-compiler-options"></a>-platform (C# Derleyici Seçenekleri)
Hangi sürümü ortak dil çalışma zamanı (CLR), derleme çalıştırılıp belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-platform:string  
```  
  
## <a name="parameters"></a>Parametreler  
 `string`  
 (varsayılan) anycpu, anycpu32bitpreferred, ARM, x 64, x86 ya da Itanium.  
  
## <a name="remarks"></a>Açıklamalar  
  
-   **anycpu** (varsayılan), derlemenizi herhangi bir platform üzerinde çalıştırmasını derler. Uygulamanız bir 64 bit işlem olarak mümkün olduğunda çalışır ve bu mod yalnızca 32-bit zaman geri döner.  
  
-   **anycpu32bitpreferred** derlemenizi herhangi bir platformda çalıştırmak için. Uygulamanızı hem 64-bit ve 32-bit uygulamaları destekleyen sistemlerde 32-bit modunda çalıştırır. .NET Framework 4.5 hedefleyen projeler için yalnızca bu seçeneği belirtebilirsiniz.  
  
-   **ARM** derlemenizi Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayar üzerinde çalıştırılacak.  
  
-   **ARM64** derlemenizi 64 bit CLR tarafından A64 yönerge kümesini destekleyen bir Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayar üzerinde çalıştırılacak.  

-   **x64** derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayara 64 bit CLR tarafından çalıştırılacak.  
  
-   **x86** derlemenizi 32-bit, x86 ile uyumlu bir CLR tarafından çalıştırılacak.  
  
-   **Itanium** derlemenizi 64 bit CLR tarafından bir Itanium işlemci bir bilgisayarda çalıştırılması.  
  
 Bir 64 bit Windows işletim sisteminde:  
  
-   Derlenmiş derlemelerde **-platform: x 86** WOW64 altında çalışan 32 bitlik CLR üzerinde yürütün.  
  
-   Bir DLL ile derlenmiş **-platform: anycpu** içine yüklendiği işlem olarak aynı CLR üzerinde çalıştırır.  
  
-   İle derlenen yürütülebilir dosyaları **-platform: anycpu** 64 bitlik CLR yürütün.  
  
-   Yürütülebilir dosyalar ile derlenmiş olan **-platform: anycpu32bitpreferred** 32 bitlik CLR yürütün.  
  
 **Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosya için geçerlidir (. EXE) dosyaları ve .NET Framework 4.5 gerektirir.  
  
 Bir Windows 64-bit işletim sisteminde çalıştırılacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Açık **özellikleri** proje sayfası.  
  
2. Tıklayın **derleme** özellik sayfası.  
  
3. Değiştirme **Platform hedefi** özelliği ve .NET Framework 4.5 hedefleyen projeler için seçin veya temizleyin **32 bit tercih et** onay kutusu.  
  
 **Not - platform** Visual C# Express geliştirme ortamında kullanılamaz.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir **-platform** uygulama 64 bitlik CLR tarafından bir 64 bit Windows işletim sisteminde çalıştırılması gerektiğini belirtmek için seçeneği.  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
