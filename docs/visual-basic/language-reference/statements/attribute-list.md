---
title: Öznitelik Listesi
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f9332f52622551bb6b944242f71bd80f439982e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354055"
---
# <a name="attribute-list-visual-basic"></a>Öznitelik Listesi (Visual Basic)
Belirtilen bir programlama öğesine uygulanacak öznitelikleri belirtir. Birden çok öznitelik virgülle ayrılır. Bir özniteliğin sözdizimi aşağıda verilmiştir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Bölümler  
|||
|---|---|
|`attributemodifier`|Kaynak dosyanın başlangıcında uygulanan öznitelikler için gereklidir. [Bütünleştirilmiş kod](../../../visual-basic/language-reference/modifiers/assembly.md) veya [Modül](../../../visual-basic/language-reference/modifiers/module-keyword.md)olabilir.|
|`attributename`| Gerekli. Özniteliğin adı.|
|`attributearguments`|İsteğe bağlı. Bu öznitelik için Konumsal bağımsız değişkenlerin listesi. Birden çok bağımsız değişken virgülle ayrılır.|
|`attributeinitializer`|İsteğe bağlı. Bu öznitelik için değişken veya özellik başlatıcıları listesi. Birden çok Başlatıcı virgülle ayrılır.|
  
## <a name="remarks"></a>Açıklamalar  
 Neredeyse tüm programlama öğeleri (türler, yordamlar, özellikler vb.) için bir veya daha fazla öznitelik uygulayabilirsiniz. Öznitelikler, derlemenizin meta verilerinde görünür ve kodunuza açıklama eklemek veya belirli bir programlama öğesinin nasıl kullanılacağını belirtmek için yardımcı olabilirler. Visual Basic ve .NET Framework tarafından tanımlanan öznitelikleri uygulayabilir ve kendi öznitelerinizi tanımlayabilirsiniz.  

 Özniteliklerin ne zaman kullanılacağı hakkında daha fazla bilgi için bkz. [özniteliklere genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md). Öznitelik adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Yerleştirilmesine.** Öznitelikleri, en çok tanımlanmış programlama öğelerine uygulayabilirsiniz. Bir veya daha fazla öznitelik uygulamak için, öğe bildiriminin başlangıcına bir *öznitelik bloğu* yerleştirebilirsiniz. Öznitelik listesindeki her giriş, uygulamak istediğiniz bir özniteliği ve bu özniteliğin çağrılması için kullandığınız değiştirici ve bağımsız değişkenleri belirtir.  
  
- **Açılı ayraçlar.** Bir öznitelik listesi sağlarsanız, onu açılı ayraç içine almalısınız ("`<`" ve "`>`").  
  
- **Bildirimin bir parçası.** Öznitelik, ayrı bir ifadeye değil, öğe bildiriminin bir parçası olmalıdır. Bildirim ifadesini birden çok kaynak kodu satırı üzerine genişletmek için satır devamlılık sırasını ("`_`") kullanabilirsiniz.  
  
- **İlerine.** Bir kaynak dosyasının başındaki bir programlama öğesine uygulanan her öznitelikte bir öznitelik değiştiricisi (`Assembly` veya `Module`) gereklidir. Kaynak dosyanın başlangıcında olmayan öğelere uygulanan özniteliklerde öznitelik değiştiricilerine izin verilmez.  
  
- **Değişkenlerinden.** Bir özniteliğin tüm Konumsal bağımsız değişkenleri herhangi bir değişken veya özellik başlatıcıdan önce gelmelidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğini bir `Function` yordamının iskelet tanımına uygular.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>, öznitelikli yordamın yönetilmeyen dinamik bağlantı kitaplığındaki (DLL) bir giriş noktasını temsil ettiğini belirtir. Özniteliği bir konum bağımsız değişkeni olarak DLL adını ve değişken başlatıcıları olarak diğer bilgileri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Derleme](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Modül \<anahtar sözcüğü >](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Özniteliklere genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
