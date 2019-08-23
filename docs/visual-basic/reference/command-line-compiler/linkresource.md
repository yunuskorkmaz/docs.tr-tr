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
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924853"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Yönetilen bir kaynağa bir bağlantı oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Gerekli. Derlemeye bağlanacak kaynak dosyası. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.  
  
 `identifier`  
 İsteğe bağlı. Kaynağın mantıksal adı. Kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. İsteğe bağlı olarak, dosyanın derleme bildiriminde genel mi yoksa özel mi olduğunu belirtebilirsiniz, örneğin: `-linkres:filename.res,myname.res,public`. Varsayılan olarak, `filename` derlemede ortaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu seçenek, kaynak dosyasını çıkış dosyasına eklemez; bunu yapmak için `-resource` seçeneğini kullanın. `-linkresource`  
  
 Seçeneği `-linkresource` , dışındaki `-target` seçeneklerden `-target:module`birini gerektirir.  
  
 , Örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. `filename` (Daha fazla bilgi için bkz <xref:System.Resources.ResourceManager>..) Çalışma zamanında diğer tüm kaynaklara erişmek için `GetManifestResource` <xref:System.Reflection.Assembly> sınıfında başlayan yöntemleri kullanın.  
  
 Dosya adı herhangi bir dosya biçimi olabilir. Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.  
  
 `-linkresource` Öğesinin`-linkres`kısa biçimi.  
  
> [!NOTE]
> Bu `-linkresource` seçenek, Visual Studio geliştirme ortamından kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `in.vb` ve kaynak dosyasına `rf.resource`bağlanır.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-Kaynak (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
