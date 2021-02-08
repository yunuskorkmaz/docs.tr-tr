---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: varlıkları seri hale getirme'
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: cb2253d7933f3584543b4b030bc8b5aa3cc62921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785945"
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
