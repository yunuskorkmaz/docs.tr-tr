---
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25c9c1c81db0bb6775aa9226318d7ec726a93e09
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924934"
---
# <a name="xslt-extension-objects"></a>XSLT Genişletme Nesneleri
Uzantı nesneleri stil sayfalarının işlevlerini genişletmek için kullanılır. Uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> sınıfı tarafından korunur.  
  
 Katıştırılmış betik yerine uzantı nesnesi kullanmanın avantajları aşağıda verilmiştir:  
  
- Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.  
  
- Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.  
  
 XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> nesnesine <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi kullanılarak eklenir. Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> Yöntemi çağırmak için FullTrust izin kümesi gereklidir. Daha fazla bilgi için bkz. [kod erişimi güvenliği](../../../../docs/framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Uzantı nesnelerinden döndürülen `number`veri türleri `Boolean`, `string`,, ve `node set`' nin dört temel XPath veri türünden biridir.  
  
 Belirtilmemiş bir parametre sayısının geçirilmesine izin veren `params` anahtar sözcüğü ile tanımlanmış herhangi bir yöntem, şu anda <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı tarafından desteklenmemektedir. `params` Anahtar sözcükle tanımlanmış herhangi bir yöntemi kullanan XSLT stil sayfaları doğru çalışmaz. Ayrıntılar için bkz. [params](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT uzantı nesnesi kullanmak için  
  
1. Bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve yöntemi kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> Uzantı nesnesini ekleyin.  
  
2. Uzantı nesnesini stil sayfasından çağırın.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> Nesneyi<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XSLT Güvenlik Konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md)
