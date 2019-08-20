---
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
ms.openlocfilehash: 454915454f3faf15933257f3e3e221afec51d0ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606760"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (C# derleyici seçenekleri)
Çıkış dosyasındaki bir .NET Framework kaynağına bir bağlantı oluşturur. Kaynak dosyası çıkış dosyasına eklenmez. Bu, çıkış dosyasına bir kaynak dosyası katıştırabilen [-Resource](./resource-compiler-option.md) seçeneğinden farklıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Derlemeden bağlamak istediğiniz .NET Framework kaynak dosyası.  
  
 `identifier`seçim  
 Kaynağın mantıksal adı; kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır.  
  
 `accessibility-modifier`seçim  
 Kaynağın erişilebilirliği: public veya Private. Varsayılan değer geneldir.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, bağlantılı kaynaklar C# derleyici ile oluşturulduklarında derlemede ortaktır. Kaynakları özel hale getirmek için erişilebilirlik değiştiricisi `private` olarak belirtin. `public` Veya`private` dışında başka bir değiştirici kullanılamaz.  
  
 **-linkresource** ,- **target: Module**dışındaki [-target](./target-compiler-option.md) seçeneklerinden birini gerektiriyor.  
  
 , Örneğin [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename` Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, çalışma zamanında `GetManifestResource` kaynağa erişmek üzere <xref:System.Reflection.Assembly> sınıfındaki yöntemleri kullanın.  
  
 İçinde `filename` belirtilen dosya herhangi bir biçimde olabilir. Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz. Aşağıdaki örneklerden İkincisi bunun nasıl yapılacağını gösterir. Derleme bağlayıcıda aynı şeyi yapabilirsiniz. Aşağıdaki örneklerden üçüncüsü bunun nasıl yapılacağını gösterir. Daha fazla bilgi için bkz. [al. exe (bütünleştirilmiş kod bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** , **-linkresource**öğesinin kısa biçimidir.  
  
 Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Derle `in.cs` ve kaynak dosyasına `rf.resource`bağla:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Örnek  
 Bir `A.cs` dll 'de derleyin, yerel dll N. dll ' ye bağlanın ve çıktıyı genel derleme önbelleği 'ne (GAC) yerleştirin. Bu örnekte, hem. dll hem de N. dll GAC 'de yer alır.  
  
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

- [C# Derleyici Seçenekleri](./index.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md)
- [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
