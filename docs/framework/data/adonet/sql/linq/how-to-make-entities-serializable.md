---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: f4528cab21ac678f5d06717d0ce6e7ff7e77d3e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203507"
---
# <a name="how-to-make-entities-serializable"></a>Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme

Kodunuzu oluştururken varlıkları seri hale getirilebilir hale getirebilirsiniz. Varlık sınıfları özniteliğiyle <xref:System.Runtime.Serialization.DataContractAttribute> ve özniteliğiyle birlikte sütunlar halinde tasarlanmalıdır <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 Visual Studio kullanan geliştiriciler bu amaçla Nesne İlişkisel Tasarımcısı kullanabilir.  
  
 SQLMetal komut satırı aracını kullanıyorsanız, **/Serialization** seçeneğini `unidirectional` bağımsız değişkeniyle birlikte kullanın. Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
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
