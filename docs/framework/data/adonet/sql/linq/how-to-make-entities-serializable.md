---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: bbe40ec448bef5f62d4182d96f82c6308639e27f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086773"
---
# <a name="how-to-make-entities-serializable"></a>Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme
Kodunuzu oluşturduğunuzda, varlıkları serileştirilebilir yapabilirsiniz. Varlık sınıfları ile düzenlenmiş <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği ve sütunları <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.  
  
 Visual Studio kullanan geliştiricilerin kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu amaç için.  
  
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
