---
title: XSLT uzantısı nesneleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: 3
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 72b1605c6bc5a0f3cbc4417d043ab21bf0bb787e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="xslt-extension-objects"></a>XSLT uzantısı nesneleri
Uzantı nesneler, stil sayfaları işlevselliğini genişletmek için kullanılır. Uzantı nesneleri tarafından korunduğundan <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.  
  
 Katıştırılmış betik yerine bir uzantı nesnesi kullanmanın avantajları şunlardır:  
  
-   Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.  
  
-   Stil sayfaları, küçük ve daha rahat olmasını sağlar.  
  
 XSLT uzantısı nesnelerinin eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak nesne <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. Bir tam adı ve ad alanı URI'si o anda uzantısı nesne ile ilişkili.  
  
> [!NOTE]
>  FullTrust izin kümesi çağırmak için gerekli <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. Daha fazla bilgi için bkz: [kod erişim güvenliği](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) ve [NIB: adlandırılmış izin kümeleri](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Dört temel XPath veri türlerinden birini uzantısı nesnelerden döndürülen veri türleri: `number`, `string`, `Boolean`, ve `node set`.  
  
 İle tanımlanmış herhangi bir yöntemini `params` belirsiz sayıda iletilecek parametre veren anahtar sözcüğü, şu anda desteklenmiyor tarafından <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. İle tanımlanmış herhangi bir yöntemini kullanan XSLT stil sayfaları `params` anahtar sözcüğü düzgün çalışmaz. Ayrıntılar için bkz [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT uzantı nesnesi kullanmak için  
  
1.  Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesnesini ve nesne uzantısını kullanarak ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.  
  
2.  Uzantı nesnesi stil sayfası içinden çağırın.  
  
3.  Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [XSLT Güvenlik Konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md)
