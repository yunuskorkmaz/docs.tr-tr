---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005492"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Yönetilen bir kaynağa bir bağlantı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

veya  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Gerekli. Derlemeye bağlanacak kaynak dosyası. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.  
  
 `identifier`  
 İsteğe bağlı. Kaynağın mantıksal adı. Kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. İsteğe bağlı olarak, dosyanın derleme bildiriminde genel mi yoksa özel mi olduğunu belirtebilirsiniz, örneğin: `-linkres:filename.res,myname.res,public`. Varsayılan olarak, `filename`, derlemede ortaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 seçeneği, kaynak dosyasını çıkış dosyasına eklemez; Bunu yapmak için `-resource` seçeneğini kullanın.  
  
 @No__t-0 seçeneği, `-target:module` dışındaki @no__t 1 seçenekten birini gerektirir.  
  
 @No__t-0, örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. (Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager>.) Çalışma zamanında diğer tüm kaynaklara erişmek için, <xref:System.Reflection.Assembly> sınıfında `GetManifestResource` ile başlayan yöntemleri kullanın.  
  
 Dosya adı herhangi bir dosya biçimi olabilir. Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.  
  
 @No__t-0 ' ın kısa biçimi `-linkres` ' dir.  
  
> [!NOTE]
> @No__t-0 seçeneği, Visual Studio geliştirme ortamında kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `in.vb` ve `rf.resource` kaynak dosyasının bağlantılarını derler.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
