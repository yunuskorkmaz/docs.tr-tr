---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793557"
---
# <a name="how-to-make-entities-serializable"></a>Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme
Kodunuzu oluştururken varlıkları seri hale getirilebilir hale getirebilirsiniz. Varlık sınıfları özniteliğiyle ve <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğiyle birlikte sütunlar halinde tasarlanmalıdır.  
  
 Visual Studio kullanan geliştiriciler bu amaçla Nesne İlişkisel Tasarımcısı kullanabilir.  
  
 SqlMetal komut satırı aracını kullanıyorsanız, **/Serialization** seçeneğini `unidirectional` bağımsız değişkeniyle birlikte kullanın. Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQLMetal komut satırları, serileştirilebilir varlıkları olan dosyaları oluşturur.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme](serialization.md)
- [Nesne Modeli Oluşturma](creating-the-object-model.md)
