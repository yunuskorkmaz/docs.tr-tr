---
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 03e24153cc11c139fc9d9e692ef93bd82c51ee3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282603"
---
# <a name="xslt-extension-objects"></a>XSLT Genişletme Nesneleri
Uzantı nesneleri stil sayfalarının işlevlerini genişletmek için kullanılır. Uzantı nesneleri sınıfı tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> .  
  
 Katıştırılmış betik yerine uzantı nesnesi kullanmanın avantajları aşağıda verilmiştir:  
  
- Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.  
  
- Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.  
  
 XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> nesnesine yöntemi kullanılarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.  
  
> [!NOTE]
> Yöntemi çağırmak için FullTrust izin kümesi gereklidir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Daha fazla bilgi için bkz. [kod erişimi güvenliği](../../../framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Uzantı nesnelerinden döndürülen veri türleri,,, ve ' nin dört temel XPath veri türünden biridir `number` `string` `Boolean` `node set` .  
  
 `params`Belirtilmemiş bir parametre sayısının geçirilmesine izin veren anahtar sözcüğü ile tanımlanmış herhangi bir yöntem, şu anda sınıfı tarafından desteklenmemektedir <xref:System.Xml.Xsl.XslCompiledTransform> . Anahtar sözcükle tanımlanmış herhangi bir yöntemi kullanan XSLT stil sayfaları `params` doğru çalışmaz. Ayrıntılar için bkz. [params](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT uzantı nesnesi kullanmak için  
  
1. Bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve yöntemi kullanarak Uzantı nesnesini ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .  
  
2. Uzantı nesnesini stil sayfasından çağırın.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList>Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](xslt-transformations.md)
- [XSLT Güvenlik Konuları](xslt-security-considerations.md)
