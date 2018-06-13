---
title: 'Nasıl yapılır: varlıklar seri hale getirilebilir hale getirin'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: c3b877df9707e0f98dbc2238d910842649def07f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354952"
---
# <a name="how-to-make-entities-serializable"></a>Nasıl yapılır: varlıklar seri hale getirilebilir hale getirin
Kodunuzu oluşturduğunuzda, varlıkları seri hale getirilebilir yapabilirsiniz. Sınıflar ile donatılmış <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği ve sütunlarla <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.  
  
 Visual Studio kullanarak geliştiricileri kullanabilir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bu amaç için.  
  
 SQLMetal komut satırı aracı kullanıyorsanız **/serialization** seçeneğini `unidirectional` bağımsız değişkeni. Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQLMetal komut satırlarını seri hale getirilebilir varlık sahip dosyalar üretin.  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Serileştirme](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md)  
 [Nesne Modeli Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
