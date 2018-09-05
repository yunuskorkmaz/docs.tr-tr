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
ms.openlocfilehash: 39955d86085b49ef503ea9ed531df9feafa648ac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524594"
---
# <a name="-addmodule-c-compiler-options"></a>-addmodule (C# Derleyici Seçenekleri)
Bu seçenek geçerli derleme için target: module anahtarı ile oluşturulmuş bir modül ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Meta veriler içeren bir çıkış dosyası. Dosyanın bir derleme bildirimi içeremez. Birden fazla dosya aktarmak için dosya adları virgül veya noktalı virgül ile ayırın.  
  
## <a name="remarks"></a>Açıklamalar  
 İle eklenen tüm modüller **- addmodule** çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında bir modülün herhangi bir dizinini belirtebilirsiniz ancak modülü, çalışma zamanında uygulama dizininde olması gerekir. Modül uygulama dizininde, çalışma zamanında değilse, erişmenizi sağlayacak bir <xref:System.TypeLoadException>.  
  
 `file` bir derlemeyi içeremez. Örneğin, çıktı dosyası oluşturulurken [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), meta verileri içeri aktarılabilir **- addmodule**.  
  
 Çıkış dosyası oluşturulurken bir **-hedef** dışında seçeneği **-target: module**, ile meta verilerini içeri aktarılamıyor **- addmodule** ancak ileiçeriaktarılabilir[-başvuru](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor; bir proje bir modüle başvuramaz. Ayrıca, bu derleyici seçeneğini program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Kaynak dosyasını derlemek `input.cs` ve meta verileri ekleme `metad1.netmodule` ve `metad2.netmodule` üretmek için `out.exe`:  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
- [Çok Dosyalı Bütünleştirilmiş Kodlar](../../../framework/app-domains/multifile-assemblies.md)  
- [Nasıl yapılır: Çok Dosyalı Bütünleştirilmiş Kod Derleme](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
