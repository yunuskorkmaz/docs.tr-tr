---
description: -addmodule (C# derleyici seçenekleri)
title: -addmodule (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: ec72fc76b3d550029b1286f64b8f86e69e721468
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150576"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (C# derleyici seçenekleri)

Bu seçenek, target: Module anahtarı geçerli derlemeye ile oluşturulmuş bir modül ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `file`, `file2`  
 Meta veri içeren bir çıkış dosyası. Dosya, bütünleştirilmiş kod bildirimi içeremez. Birden fazla dosyayı içeri aktarmak için, dosya adlarını virgülle veya noktalı virgülle ayırın.  
  
## <a name="remarks"></a>Açıklamalar  

 **-Addmodule** ile eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir. Modül, çalışma zamanında uygulama dizininde değilse, bir alırsınız <xref:System.TypeLoadException> .  
  
 `file` bütünleştirilmiş kod içeremez. Örneğin, çıkış dosyası [-target: Module](./target-module-compiler-option.md)ile oluşturulduysa, meta verileri **-addmodule**ile içeri aktarılabilir.  
  
 Çıkış dosyası **-target: Module**dışında bir **-target** seçeneği ile oluşturulduysa, meta verileri **-addmodule** ile içeri aktarılamaz ancak [-Reference](./reference-compiler-option.md)ile içeri aktarılabilir.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz; bir proje bir modüle başvuramaz. Ayrıca, bu derleyici seçeneği program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  

 Kaynak dosyasını derleyin `input.cs` , ve ' dan meta verileri ekleyin `metad1.netmodule` `metad2.netmodule` `out.exe` :  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Çoklu dosya derlemeleri](../../../framework/app-domains/multifile-assemblies.md)
- [Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme](../../../framework/app-domains/build-multifile-assembly.md)
