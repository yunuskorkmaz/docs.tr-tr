---
title: 'Nasıl yapılır: varlıklar seri hale getirilebilir hale getirin'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: b14738e5220810f01b555e54efaad8d8898b7e45
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
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
