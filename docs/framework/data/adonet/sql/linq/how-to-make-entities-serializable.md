---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: fd687ba5dce16baee063f1d3bb9521c6664988b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743282"
---
# <a name="how-to-make-entities-serializable"></a>Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme
Kodunuzu oluşturduğunuzda, varlıkları serileştirilebilir yapabilirsiniz. Varlık sınıfları ile düzenlenmiş <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği ve sütunları <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.  
  
 Visual Studio kullanan geliştiricilerin, Nesne İlişkisel Tasarımcısı bu amaç için kullanabilirsiniz.  
  
 SQLMetal komut satırı aracı kullanıyorsanız **/serialization** seçeneğini `unidirectional` bağımsız değişken. Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQLMetal komut satırları, seri hale getirilebilir varlıkların dosyaları oluşturur.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)
- [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
