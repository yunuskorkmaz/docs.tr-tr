---
title: "-linkresource (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7da5a55fa96c11d79f8c616cf0f1f4e0ed109bfa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (C# Derleyici Seçenekleri)
.NET Framework kaynağına bağlantı çıktı dosyasında oluşturur. Kaynak dosyanın çıkış dosyasına eklenmez. Bu farklıdır [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) kaynak dosyasını çıktı dosyasına katıştırma seçeneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier`(isteğe bağlı)  
 Kaynak için mantıksal ad; Kaynak yüklemek için kullanılan ad. Varsayılan dosya adıdır.  
  
 `accessibility-modifier`(isteğe bağlı)  
 Kaynak erişilebilirliğini: genel veya özel. Ortak varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 C# derleyici ile oluşturduğunuzda varsayılan olarak, bağlantılı derlemede ortak kaynaklardır. Kaynakları özel hale getirmek için belirtmeniz `private` olarak erişim değiştiricisi. Herhangi bir değiştiricisi dışında `public` veya `private` izin verilir.  
  
 **-linkresource** birini gerektirir [-hedef](../../../csharp/language-reference/compiler-options/target-compiler-option.md) dışında seçenekleri **-target: module**.  
  
 Varsa `filename` , örneğin, tarafından oluşturulan bir .NET Framework kaynak dosyası [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında üyelerle erişilebileceğini <xref:System.Resources> ad alanı. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için kullanmak `GetManifestResource` yöntemleri <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek için sınıf.  
  
 Belirtilen dosya `filename` herhangi bir biçimde olabilir. Örneğin, böylece genel derleme önbelleğine yüklü ve yönetilen kod derlemesindeki erişilen derleme yerel bir DLL parçası haline getirmek isteyebilirsiniz. Aşağıdaki örnekler ikinci bunun nasıl yapılacağı gösterilmektedir. Derleme Bağlayıcı aynı şeyi yapabilirsiniz. Aşağıdaki örnekler üçüncü bunun nasıl yapılacağı gösterilmektedir. Daha fazla bilgi için bkz: [Al.exe (derleme bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** kısa biçimi olan **- linkresource**.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamıyor ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve kaynak dosyası bağlantısı `rf.resource`:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Örnek  
 Derleme `A.cs` bir DLL içerisine bağlamak için yerel bir DLL N.dll ve çıktı Genel Derleme Önbelleği'ne (GAC) yerleştirin. Bu örnekte, hem A.dll hem de N.dll GAC'de yer alacaktır.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek önceki bir, ancak derleme bağlayıcı seçeneklerini kullanarak aynı şeyi yapar.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md)  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
