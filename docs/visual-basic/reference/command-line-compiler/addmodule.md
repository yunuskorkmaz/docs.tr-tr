---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524471"
---
# <a name="-addmodule"></a>-addmodule
Derleyicinin, belirtilen dosya (lar) dan tüm tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `fileList`  
 Gereklidir. Meta veri içeren ancak derleme bildirimleri içermeyen dosyaların virgülle ayrılmış listesi. Boşluk içeren dosya adları tırnak işaretleri ("") içine alınmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `fileList` Parametresi tarafından listelenen dosyaların `-target:module` seçeneğiyle oluşturulması veya başka bir derleyicinin eşdeğeri olması gerekir `-target:module`.  
  
 İle `-addmodule` eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir. Aksi takdirde bir <xref:System.TypeLoadException> hata alırsınız.  
  
 `-target:module` İle `-addmodule`dışında herhangi bir `-addmodule` [hedef Visual Basic (](../../../visual-basic/reference/command-line-compiler/target.md) örtük veya açık) herhangi bir seçeneği belirtirseniz, bu dosya projenin derlemesinin bir parçası haline gelir. Bir veya daha fazla dosya eklenmiş bir çıkış dosyası çalıştırmak için bütünleştirilmiş kod gereklidir `-addmodule`.  
  
 Derleme içeren bir dosyadan meta verileri içeri aktarmak için [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) kullanın.  
  
> [!NOTE]
> Bu `-addmodule` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir modül oluşturur.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 Aşağıdaki kod modülün türlerini içeri aktarır.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Çalıştırdığınızda `t1`, çıkış çıkışları `802`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-başvuru (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
