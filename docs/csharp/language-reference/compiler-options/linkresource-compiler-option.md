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
ms.openlocfilehash: 41af8e0ba8ffebd07d3cb1d2bc5fbc04b8cd595d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173737"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (C# Derleyici Seçenekleri)
Çıktı dosyasındaki bir .NET Framework kaynağına bağlantı oluşturur. Kaynak dosyası çıktı dosyasına eklenmez. Bu, çıktı dosyasına bir kaynak dosyası gömmeyi yapan [-kaynak](./resource-compiler-option.md) seçeneğinden farklıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier` (isteğe bağlı)  
 Kaynak için mantıksal ad; kaynağı yüklemek için kullanılan ad. Varsayılan, dosyanın adıdır.  
  
 `accessibility-modifier` (isteğe bağlı)  
 Kaynağın erişilebilirliği: ortak veya özel. Varsayılan değer herkese açıktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bağlı kaynaklar C# derleyicisi ile oluşturulduğunda derlemede herkese açıktır. Kaynakları özel yapmak için `private` erişilebilirlik değiştirici olarak belirtin. Başka bir değiştirici `public` dışında `private` veya izin verilir.  
  
 **-linkresource** **-target:module**dışındaki [-hedef](./target-compiler-option.md) seçeneklerinden birini gerektirir.  
  
 Örneğin `filename` [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulan bir .NET Framework kaynak dosyasıysa, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, çalışma <xref:System.Reflection.Assembly> zamanında kaynağa erişmek için sınıftaki `GetManifestResource` yöntemleri kullanın.  
  
 Belirtilen dosya `filename` herhangi bir biçimde olabilir. Örneğin, genel derleme önbelleğine yüklenmesi ve derlemedeki yönetilen koddan erişilebilmesini sağlamak için derlemenin yerel bir DLL parçası olmak isteyebilirsiniz. Aşağıdaki örneklerden ikincisi bunun nasıl yapılacağını gösterir. Aynı şeyi Derleme Linker'da da yapabilirsiniz. Aşağıdaki örneklerin üçüncüsü bunun nasıl yapılacağını gösterir. Daha fazla bilgi için [Al.exe (Derleme Bağlantı Cısı)](../../../framework/tools/al-exe-assembly-linker.md) ve [Derlemeler ve Küresel Montaj Önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)'ya bakın.  
  
 **-linkres** **-linkresource**kısa şeklidir.  
  
 Bu derleyici seçeneği Visual Studio'da kullanılamaz ve programlı olarak değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Kaynak `in.cs` dosyasını `rf.resource`derleme ve bağlantı:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Örnek  
 Bir `A.cs` DLL'ye kopyala, yerel bir DLL N.dll'ye bağlantı ve çıktıyı Global Assembly Önbelleğine (GAC) koyun. Bu örnekte, hem A.dll hem de N.dll GAC'de ikamet edecektir.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Örnek  
 Bu örnek, öncekiyle aynı şeyi yapar, ancak Derleme Bağlayıcı sı seçeneklerini kullanarak.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md)
- [Derlemeler ve Genel Derleme Önbelleği ile Çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
