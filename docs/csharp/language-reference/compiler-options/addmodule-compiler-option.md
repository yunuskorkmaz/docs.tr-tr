---
title: -addmodule (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970182"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (C# Derleyici Seçenekleri)
Bu seçenek, geçerli derlemeye hedef modülü anahtarı ile oluşturulmuş bir modül ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `file`, `file2`  
 Meta veri içeren bir çıktı dosyası. Dosya bir derleme bildirimi içeremez. Birden fazla dosya almak için, virgül veya yarı iki nokta üst üste dosya adlarını ayırın.  
  
## <a name="remarks"></a>Açıklamalar  
 **-addmodule** ile eklenen tüm modüller, çalışma zamanında çıktı dosyasıyla aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir. Modül çalışma zamanında uygulama dizininde değilse, bir <xref:System.TypeLoadException>.  
  
 `file`bir derleme içeremez. Örneğin, çıktı dosyası [-target:module](./target-module-compiler-option.md)ile oluşturulmuşsa, meta verileri **-addmodule**ile içe aktarılabilir.  
  
 Çıktı dosyası **-target:module**dışında bir **-hedef** seçeneği ile oluşturulmuşsa, meta verileri **-addmodule** ile içe aktarılamaz, ancak [-referans](./reference-compiler-option.md)ile içe aktarılabilir.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz; bir proje bir modüle başvuru yapamaz. Ayrıca, bu derleyici seçeneği programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Kaynak dosyayı `input.cs` derle ve `metad1.netmodule` `metad2.netmodule` meta `out.exe`veri ekleyin ve üretmek için:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Birden Çok Dosya Derlemeleri](../../../framework/app-domains/multifile-assemblies.md)
- [Nasıl yapılır: Birden Fazla Dosya Derlemesi Oluşturma](../../../framework/app-domains/build-multifile-assembly.md)
