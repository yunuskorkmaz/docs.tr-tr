---
title: UriTemplate Tablo Örneği
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: fb5932acce60e2da45f99730580237d31130d918
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715414"
---
# <a name="uritemplate-table-sample"></a>UriTemplate Tablo Örneği
<xref:System.UriTemplateTable> sınıfı, bir `UriTemplate` örnekleri kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar. Belirli bir Tekdüzen Kaynak tanımlayıcısı (URI), tablodaki tüm şablonlara göre etkili bir şekilde eşleştirilebilir ve eşleşen şablonla ilişkili veriler alınabilir.  
  
 Bu örnek `UriTemplateTable` sınıfıyla ilgili aşağıdaki temel kavramları gösterir:  
  
- `UriTemplateTable`örneği oluşturma sözdizimi.  
  
- Bir `UriTemplateTable` anahtar/değer çiftleri kümesiyle doldurma.  
  
- <xref:System.UriTemplateTable.MatchSingle%2A>kullanarak bir aday URI 'sini tabloyla eşleştirme.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
2. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UriTemplate Tablosu Dağıtıcısı](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
