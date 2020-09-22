---
title: Öznitelik Listesi
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: e566239c56efa8ca8e83bff92486fec4c434e92b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874736"
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
|`attributemodifier`|Kaynak dosyanın başlangıcında uygulanan öznitelikler için gereklidir. [Bütünleştirilmiş kod](../modifiers/assembly.md) veya [Modül](../modifiers/module-keyword.md)olabilir.|
|`attributename`| Gereklidir. Özniteliğin adı.|
|`attributearguments`|İsteğe bağlı. Bu öznitelik için Konumsal bağımsız değişkenlerin listesi. Birden çok bağımsız değişken virgülle ayrılır.|
|`attributeinitializer`|İsteğe bağlı. Bu öznitelik için değişken veya özellik başlatıcıları listesi. Birden çok Başlatıcı virgülle ayrılır.|
  
## <a name="remarks"></a>Açıklamalar  

 Neredeyse tüm programlama öğeleri (türler, yordamlar, özellikler vb.) için bir veya daha fazla öznitelik uygulayabilirsiniz. Öznitelikler, derlemenizin meta verilerinde görünür ve kodunuza açıklama eklemek veya belirli bir programlama öğesinin nasıl kullanılacağını belirtmek için yardımcı olabilirler. Visual Basic ve .NET Framework tarafından tanımlanan öznitelikleri uygulayabilir ve kendi öznitelerinizi tanımlayabilirsiniz.  

 Özniteliklerin ne zaman kullanılacağı hakkında daha fazla bilgi için bkz. [özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md). Öznitelik adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Kurallar  
  
- **Yerleştirilmesine.** Öznitelikleri, en çok tanımlanmış programlama öğelerine uygulayabilirsiniz. Bir veya daha fazla öznitelik uygulamak için, öğe bildiriminin başlangıcına bir *öznitelik bloğu* yerleştirebilirsiniz. Öznitelik listesindeki her giriş, uygulamak istediğiniz bir özniteliği ve bu özniteliğin çağrılması için kullandığınız değiştirici ve bağımsız değişkenleri belirtir.  
  
- **Açılı ayraçlar.** Bir öznitelik listesi sağlarsanız, onu açılı ayraç (" `<` " ve " `>` ") içine almalısınız.  
  
- **Bildirimin bir parçası.** Öznitelik, ayrı bir ifadeye değil, öğe bildiriminin bir parçası olmalıdır. `_`Bildirim ifadesini birden çok kaynak kodu satırı üzerine genişletmek için satır devamlılığı sırasını ("") kullanabilirsiniz.  
  
- **İlerine.** Bir `Assembly` `Module` kaynak dosyasının başındaki bir programlama öğesine uygulanan her öznitelikte bir öznitelik değiştiricisi (veya) gereklidir. Kaynak dosyanın başlangıcında olmayan öğelere uygulanan özniteliklerde öznitelik değiştiricilerine izin verilmez.  
  
- **Değişkenlerinden.** Bir özniteliğin tüm Konumsal bağımsız değişkenleri herhangi bir değişken veya özellik başlatıcıdan önce gelmelidir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Runtime.InteropServices.DllImportAttribute> bir yordamın iskelet tanımına özniteliğini uygular `Function` .  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Öznitelikli yordamın yönetilmeyen bir dinamik bağlantı kitaplığındaki (DLL) bir giriş noktasını temsil ettiğini belirtir. Özniteliği bir konum bağımsız değişkeni olarak DLL adını ve değişken başlatıcıları olarak diğer bilgileri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kod](../modifiers/assembly.md)
- [Birimi \<keyword>](../modifiers/module-keyword.md)
- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
