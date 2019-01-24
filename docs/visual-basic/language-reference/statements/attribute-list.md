---
title: Öznitelik Listesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 9ab55187fef11fba9c794ff0266656860bea3d1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672116"
---
# <a name="attribute-list-visual-basic"></a>Öznitelik Listesi (Visual Basic)
Bildirilmiş programlama öğesine uygulanacak öznitelikleri belirtir. Birden çok öznitelik virgülle ayrılır. Bir öznitelik için sözdizimi aşağıdadır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Bölümler  
|||
|---|---|
|`attributemodifier`|Bir kaynak dosyasının başında uygulanan öznitelikleri için gereklidir. Olabilir [derleme](../../../visual-basic/language-reference/modifiers/assembly.md) veya [Modülü](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`| Gerekli. Özniteliğin adı.|
|`attributearguments`|İsteğe bağlı. Bu öznitelik için konumsal bağımsız değişkenler listesi. Birden çok bağımsız değişkeni virgülle ayrılır.|
|`attributeinitializer`|İsteğe bağlı. Bu öznitelik için değişken veya özellik başlatıcıları listesi. Birden çok başlatıcılar virgülle ayrılır.|
  
## <a name="remarks"></a>Açıklamalar  
 Neredeyse tüm programlama öğesine (türleri, yordamlar, özellikleri ve benzeri) bir veya daha fazla öznitelikleri uygulayabilirsiniz. Öznitelikler, derlemenin meta verilerde görünür ve kodunuzu Not ekleme ya da belirli bir programlama öğesinin nasıl kullanılacağını belirtin yardımcı olabilir. Visual Basic ve .NET Framework tarafından tanımlanan öznitelikleri uygulayabilirsiniz ve kendi öznitelikler tanımlayabilirsiniz.  

 Ne zaman öznitelikleri kullanma hakkında daha fazla bilgi için bkz. [öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md). Öznitelik adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Yerleştirme.** En bildirilmiş programlama öğesine için öznitelikleri uygulayabilirsiniz. Bir veya daha fazla öznitelik uygulamak için yerleştirme bir *öznitelik bloğuna* öğe bildirimi başında. Öznitelik listesindeki her bir giriş, uygulamak istediğiniz bir öznitelik değiştiricisi ve bu öznitelik çağırma için kullanmakta olduğunuz bağımsız değişkenleri belirtir.  
  
-   **Açılı ayraçlar.** Bir öznitelik listesi sağlarsanız, açılı ayraçlar içine gerekir ("`<`"ve"`>`").  
  
-   **Bildiriminin bir parçası.** Öznitelik, öğe bildirimi, ayrı bir bildirimi bir parçası olması gerekir. Satır devamlılığı sırası kullanabilirsiniz (" `_`") bildirim deyimindeki birden çok kaynak kod satırlarına genişletmek için.  
  
-   **Değiştiriciler.** Bir öznitelik değiştirici (`Assembly` veya `Module`) bir kaynak dosyasının başında programlama öğesine uygulanan her bir öznitelik için gereklidir. Bir kaynak dosyasının başında olmayan öğelere uygulanan öznitelikleri üzerinde öznitelik değiştiricilere izin verilmez.  
  
-   **Bağımsız değişkenler.** Bir öznitelik için konumsal bağımsız değişkenler, herhangi bir değişken veya özellik başlatıcıları gelmelidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek geçerli <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği için iskelet tanımını bir `Function` yordamı.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Öznitelikli yordamı yönetilmeyen bir dinamik bağlantı kitaplığı (DLL) bir giriş noktası temsil ettiğini gösterir. Öznitelik, konumsal bağımsız değişken olarak DLL adı ve diğer bilgileri değişken başlatıcılar olarak sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Modül \<anahtar sözcüğü >](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
