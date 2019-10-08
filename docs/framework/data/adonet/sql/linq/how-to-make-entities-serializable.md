---
title: 'Nasıl yapılır: varlıkları serileştirilebilir yapma'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002703"
---
# <a name="how-to-make-entities-serializable"></a>Nasıl yapılır: varlıkları serileştirilebilir yapma
Kodunuzu oluştururken varlıkları seri hale getirilebilir hale getirebilirsiniz. Varlık sınıfları <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğiyle ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine sahip sütunlarda tasarlanmalıdır.  
  
 Visual Studio kullanan geliştiriciler bu amaçla Nesne İlişkisel Tasarımcısı kullanabilir.  
  
 SQLMetal komut satırı aracını kullanıyorsanız, **/Serialization** seçeneğini `unidirectional` bağımsız değişkeniyle birlikte kullanın. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQLMetal komut satırları, serileştirilebilir varlıkları olan dosyaları oluşturur.  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme](serialization.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
