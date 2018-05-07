---
title: -delaysign (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: f8525a4e96d172709673b94316b06d815535805f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (C# Derleyici Seçenekleri)
Bu seçenek, böylece bir dijital imza daha sonra eklenebilir çıktı dosyasında yer ayırmak için derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-delaysign[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Kullanım **- delaysign-** tam imzalı bir derleme istiyorsanız. Kullanım **- delaysign +** yalnızca ortak anahtar derlemede yerleştirmek istiyorsanız. Varsayılan değer **- delaysign-**.  
  
## <a name="remarks"></a>Açıklamalar  
 **- Delaysign** seçeneği hiçbir etkisi ile kullanılmadığı sürece [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) veya [- keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  
  
 Tam imzalı bir derleme istediğinde bildirimi (derleme meta verilerini) içeren ve karmayı özel anahtarıyla imzalar dosyayı derleyici karma hale getirir. Elde edilen dijital imza, bildirimi içeren dosyada depolanır. Bir derlemeyi imzalı gecikme olduğunda derleyici işlem değil ve daha sonra imzanın eklenmesi için imza ancak yer ayırır dosyasında depolamak.  
  
 Örneğin, kullanarak **- delaysign +** genel önbelleğinde derleme yerleştirilecek tester sağlar. Sınama sonra tam olarak derleme özel anahtarı kullanarak derlemeye koyarak oturum [derleme bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programı.  
  
 Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Açık **özellikleri** projesi için sayfa.  
  
2.  Değiştirme **gecikme yalnızca oturum** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
