---
description: -linkresource (C# derleyici seçenekleri)
title: -linkresource (C# derleyici seçenekleri)
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
ms.openlocfilehash: 4efa0cbf286b40ad971bad66a7acce15e553eb39
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194108"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (C# derleyici seçenekleri)

Çıkış dosyasında .NET kaynağına bir bağlantı oluşturur. Kaynak dosyası çıkış dosyasına eklenmez. Bu, çıkış dosyasına bir kaynak dosyası katıştırabilen [-Resource](./resource-compiler-option.md) seçeneğinden farklıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `filename`  
 Derlemeden bağlamak istediğiniz .NET kaynak dosyası.  
  
 `identifier` (isteğe bağlı)  
 Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır.  
  
 `accessibility-modifier` (isteğe bağlı)  
 Kaynağın erişilebilirliği: public veya Private. Varsayılan değer geneldir.  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, bağlı kaynaklar C# derleyicisi ile oluşturulduklarında derlemede ortaktır. Kaynakları özel hale getirmek için `private` erişilebilirlik değiştiricisi olarak belirtin. Veya dışında başka bir değiştirici `public` `private` kullanılamaz.  
  
 **-linkresource** ,- **target: Module**dışındaki [-target](./target-compiler-option.md) seçeneklerinden birini gerektiriyor.  
  
 `filename`Örneğin, [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .net kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, `GetManifestResource` <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek üzere sınıfındaki yöntemleri kullanın.  
  
 İçinde belirtilen dosya `filename` herhangi bir biçimde olabilir. Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz. Aşağıdaki örneklerden İkincisi bunun nasıl yapılacağını gösterir. Derleme bağlayıcıda aynı şeyi yapabilirsiniz. Aşağıdaki örneklerden üçüncüsü bunun nasıl yapılacağını gösterir. Daha fazla bilgi için bkz. [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** , **-linkresource**öğesinin kısa biçimidir.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  

 Derle `in.cs` ve kaynak dosyasına bağla `rf.resource` :  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Örnek  

 `A.cs`DLL 'de derleyin, yerel BIR dll N.dll bağlayın ve çıktıyı genel derleme önbelleği 'ne (GAC) yerleştirin. Bu örnekte, A.dll ve N.dll her ikisi de GAC 'de yer alır.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Örnek  

 Bu örnek, bir önceki ile aynı şeyi, ancak derleme bağlayıcı seçeneklerini kullanarak yapar.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md)
- [Derlemeler ve Genel Derleme Önbelleği ile Çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
