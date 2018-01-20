---
title: "-platform (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a7a505f955f1faf73198b3670754dbb492ff638
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-platform-c-compiler-options"></a>-platform (C# Derleyici Seçenekleri)
Ortak dil çalışma zamanı (CLR), hangi sürümünün derlemeyi çalıştırabileceğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a>Parametreler  
 `string`  
 anycpu (varsayılan), anycpu32bitpreferred, ARM, x 64, x86 ya da Itanium.  
  
## <a name="remarks"></a>Açıklamalar  
  
-   **anycpu** (varsayılan) herhangi bir platformda çalıştırmak için derleme derler. Uygulamanız bir 64-bit işlem olarak mümkün olduğunda çalışır ve bu modu yalnızca 32-bit zaman geri döner.  
  
-   **anycpu32bitpreferred** derlemenizi herhangi bir platformda çalıştırmak için. Uygulamanızı 32-bit modunda 64-bit ve 32-bit uygulamaları destekleyen sistemlerde çalışır. .NET Framework 4.5 hedefleyen projeler için yalnızca bu seçenek belirtebilirsiniz.  
  
-   **ARM** derlemenizi Gelişmiş RISC makinesi (ARM) işlemciye sahip bir bilgisayarda çalıştırmak için.  
  
-   **x64** derlemenizi AMD64 veya EM64T yönerge kümesi destekleyen bir bilgisayarda 64-bit CLR tarafından çalıştırılacak.  
  
-   **x86** derlemenizi 32-bit, x86 uyumlu CLR tarafından çalıştırılacak.  
  
-   **Itanium** derlemenizi 64-bit CLR tarafından Itanium işlemcili bir bilgisayarda çalıştırılması için.  
  
 Bir 64-bit Windows işletim sisteminde:  
  
-   Derlenmiş derlemeler **-platform: x 86** WOW64 altında çalışan 32 bit CLR yürütün.  
  
-   DLL ile derlenmiş **-platform: anycpu** aynı CLR içine yüklendiği bir işlem olarak yürütür.  
  
-   İle derlenmiş yürütülebilir dosyalar **-platform: anycpu** 64-bit CLR yürütün.  
  
-   Derlenmiş olan yürütülebilir dosyalar **-platform: anycpu32bitpreferred** 32-bit CLR yürütün.  
  
 **Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosyası için geçerlidir (. EXE) dosyaları ve .NET Framework 4.5 gerektirir.  
  
 Bir Windows 64-bit işletim sisteminde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz: [64-bit uygulamalar](../../../framework/64-bit-apps.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Açık **özellikleri** projesi için sayfa.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Değiştirme **Platform hedefi** özelliği ve .NET Framework 4.5 hedefleyen projeler seçin veya temizleyin **tercih 32-bit** onay kutusu.  
  
 **Not - platform** Visual C# Express geliştirme ortamında kullanılamaz.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir **-platform** seçeneği uygulamayı 64-bit CLR tarafından bir 64-bit Windows işletim sisteminde çalıştırılması gerektiğini belirtin.  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
