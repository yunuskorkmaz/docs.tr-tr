---
title: Öznitelik Listesi (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604081"
---
# <a name="attribute-list-visual-basic"></a>Öznitelik Listesi (Visual Basic)
Bildirilen bir programlama öğesi uygulanacak özniteliklerini belirtir. Birden çok öznitelik virgülle ayrılır. Aşağıdaki bir öznitelik sözdizimi aşağıdaki gibidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Bölümler  
 `attributemodifier`  
 Bir kaynak dosyasının başında uygulanan öznitelikleri için gereklidir. Olabilir [derleme](../../../visual-basic/language-reference/modifiers/assembly.md) veya [Modülü](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Gerekli. Özniteliğin adı.  
  
 `attributearguments`  
 İsteğe bağlı. Bu öznitelik için konumsal bağımsız değişkenler listesi. Birden çok bağımsız değişkenleri virgülle ayrılır.  
  
 `attributeinitializer`  
 İsteğe bağlı. Bu öznitelik için değişkenin veya özelliğin başlatıcıları listesi. Birden çok başlatıcıları virgülle ayrılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Neredeyse tüm programlama öğeye (türleri, yordamlar, özellikleri ve benzeri) bir veya daha fazla öznitelik uygulayabilirsiniz. Öznitelikleri, derlemenin meta verilerde görünür ve kodunuzu açıklama veya belirli bir programlama öğesinin nasıl kullanılacağını belirtmek yardımcı olabilir. Visual Basic ve .NET Framework tarafından tanımlanan öznitelikleri uygulayabilirsiniz ve kendi özniteliklerini tanımlayabilirsiniz.  

 Zaman öznitelikleri kullanılacağı hakkında daha fazla bilgi için bkz: [öznitelikleri genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md). Öznitelik adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Yerleştirme.** Öznitelikleri en bildirilen programlama öğelerine uygulayabilirsiniz. Bir veya daha fazla öznitelik uygulamak için yerleştirdiğiniz bir *öznitelik blok* öğe bildirimi başındaki. Öznitelik listesindeki her giriş uygulanmasını istediğiniz bir öznitelik ve değiştirici ve bağımsız değişkenler, bu öznitelik çağırma için kullanmakta olduğunuz belirtir.  
  
-   **Açılı ayraçları.** Bir öznitelik listesi sağlarsanız, açılı ayraçlar içine gerekir ("`<`"ve"`>`").  
  
-   **Bildirim bölümü.** Öznitelik öğe bildiriminin, ayrı bir deyimi bir parçası olması gerekir. Satır devamlılığı sırası kullanabilirsiniz (" `_`") bildirim deyiminin birden fazla kaynak kodu satır üzerine genişletmek için.  
  
-   **Değiştirici.** Bir öznitelik değiştiricisi (`Assembly` veya `Module`) bir programlama öğesi bir kaynak dosyasının başında uygulanan her bir özniteliği gereklidir. Öznitelik değiştiricileri kaynak dosyasının başında olmayan öğelere uygulanan öznitelikleri izin verilmez.  
  
-   **Bağımsız değişkenler.** Bir öznitelik için tüm konumsal bağımsız değişken veya özellik başlatıcıları gelmelidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek uygular <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği bir iskelet tanımına bir `Function` yordamı.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> Öznitelikli yordamı yönetilmeyen bir dinamik bağlantı kitaplığı (DLL) bir giriş noktası temsil ettiğini gösterir. Öznitelik konumsal bağımsız değişkeni olarak DLL adı ve diğer bilgileri değişken başlatıcılar olarak sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Modül \<anahtar sözcüğü >](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
