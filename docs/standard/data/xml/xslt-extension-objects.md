---
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2efe31ce8ece241bdfeb95687c5496c7ba0fd626
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615295"
---
# <a name="xslt-extension-objects"></a>XSLT Genişletme Nesneleri
Uzantı nesneler, stil sayfaları genişletmek için kullanılır. Genişletme nesneleri tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.  
  
 Ekli komut dosyası yerine bir uzantı nesnesi kullanmanın avantajları şunlardır:  
  
- Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.  
  
- Stil sayfaları, daha küçük ve daha rahat olmasını sağlar.  
  
 XSLT genişletme nesneleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak nesne <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. Bir tam adı ve ad alanı URI o anda uzantısı nesnesi ile ilişkilendirilmiş.  
  
> [!NOTE]
>  FullTrust izin kümesi çağrı için gerekli <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. Daha fazla bilgi için [kod erişim güvenliği](../../../../docs/framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Uzantı nesnelerinden döndürülen veri türleri dört temel XPath veri türlerinden biri: `number`, `string`, `Boolean`, ve `node set`.  
  
 Herhangi bir yöntemi ile tanımlanmış `params` geçirilecek parametreler belirtilmemiş bir sayısını veren anahtar sözcüğü, şu anda desteklenmiyor tarafından <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Herhangi bir yöntemi ile tanımlanmış yazılımınız XSLT stil sayfalarını `params` anahtar sözcüğü doğru şekilde çalışmaz. Ayrıntılar için bkz [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT uzantı nesnesi kullanmak için  
  
1. Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve uzantısını kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.  
  
2. Uzantı nesnesi stil sayfası içinden çağırın.  
  
3. Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XSLT Güvenlik Konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md)
