---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 43ebb61efa26ed11af573e2c4e73a6fd71ac0902
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403206"
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
 Gereklidir. Derlemeye bağlanacak kaynak dosyası. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.  
  
 `identifier`  
 İsteğe bağlı. Kaynağın mantıksal adı. Kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. İsteğe bağlı olarak, dosyanın derleme bildiriminde genel mi yoksa özel mi olduğunu belirtebilirsiniz, örneğin: `-linkres:filename.res,myname.res,public` . Varsayılan olarak, `filename` derlemede ortaktır.  
  
## <a name="remarks"></a>Açıklamalar  
 `-linkresource`Bu seçenek, kaynak dosyasını çıkış dosyasına eklemez; `-resource` bunu yapmak için seçeneğini kullanın.  
  
 Seçeneği, dışındaki `-linkresource` seçeneklerden birini gerektirir `-target` `-target:module` .  
  
 , `filename` Örneğin, [Resgen. exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. (Daha fazla bilgi için bkz <xref:System.Resources.ResourceManager> ..) Çalışma zamanında diğer tüm kaynaklara erişmek için sınıfında başlayan yöntemleri kullanın `GetManifestResource` <xref:System.Reflection.Assembly> .  
  
 Dosya adı herhangi bir dosya biçimi olabilir. Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz.  
  
 Öğesinin kısa biçimi `-linkresource` `-linkres` .  
  
> [!NOTE]
> `-linkresource`Bu seçenek, Visual Studio geliştirme ortamından kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `in.vb` ve kaynak dosyasına bağlanır `rf.resource` .  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-target (Visual Basic)](target.md)
- [-Kaynak (Visual Basic)](resource.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
