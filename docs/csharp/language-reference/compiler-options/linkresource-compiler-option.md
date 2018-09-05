---
title: -linkresource (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: feca4713fe0e704799e2abbae3818edd0f3a5c84
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523181"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (C# Derleyici Seçenekleri)
Çıkış dosyasında .NET Framework kaynağına bağlantı oluşturur. Kaynak dosyası çıkış dosyasına eklenmez. Bu farklıdır [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) kaynak dosyası çıkış dosyasına ekleme seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier` (isteğe bağlı)  
 Kaynağın mantıksal adı; Kaynak yüklemek için kullanılan ad. Varsayılan dosya adıdır.  
  
 `accessibility-modifier` (isteğe bağlı)  
 Kaynak erişilebilirliğini: genel veya özel. Genel varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, C# derleyicisi ile oluşturulduğunda bağlı kaynaklar derleme içinde geneldir. Kaynakları özel hale getirmek için belirtin `private` erişilebilirlik değiştiricisi olarak. Dışında bir değiştiriciye `public` veya `private` izin verilir.  
  
 **-linkresource** birini gerektirir [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri **-target: module**.  
  
 Varsa `filename` , örneğin, tarafından oluşturulmuş bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.  
  
 Belirtilen dosya `filename` herhangi bir biçimde olabilir. Örneğin, böylece genel derleme önbelleğine yüklenebilir ve derlemedeki yönetilen koddan erişilebilir bütünleştirilmiş kodun yerel bir DLL parçası haline getirmek isteyebilirsiniz. Aşağıdaki örnekler, ikinci bunun nasıl yapılacağı gösterilmektedir. Assembly Linker kullanarak aynı şeyi yapabilirsiniz. Aşağıdaki örnekler, üçüncü bunun nasıl yapılacağı gösterilmektedir. Daha fazla bilgi için [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** öğesinin kısa biçimidir **- linkresource**.  
  
 Bu derleyici seçeneğini Visual Studio'da kullanılamıyor ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve kaynak dosyasının bağlantısını `rf.resource`:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Örnek  
 Derleme `A.cs` bir DLL içine bağlantısını için yerel bir DLL N.dll ve Genel Derleme Önbelleği'ne (GAC) çıktı yerleştirin. Bu örnekte, A.dll hem N.dll GAC içinde yer alacaktır.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek Öncekine, ancak derleme bağlayıcı seçenekleri kullanarak aynı şeyi yapar.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md)  
- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
