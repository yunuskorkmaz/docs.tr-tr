---
title: ConfigurationCodeGenerator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb88d7e523c671886e3ccb0fe22d545c616e2289
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator, özel kanal uygulamaları yapılandırma sistemi için kullanıma sunmak için kullanabileceğiniz bir araçtır. Bu, kanalınızı yalnızca bunlar bir sistem tarafından sağlanan gibi bağlama yapılandırdığınız gibi bir .config dosyası kullanarak yapılandırmak, özel kanal kullanıcılarının sağlar `NetTcpBinding` veya özel bir bağlama kullanarak `TcpTransportBindingElement`.  
  
 Ne zaman özel bir kanalda yazma ve yeni bir kullanarak programlama modeli kullanıma `BindingElement` veya `Binding`, yapmak için sınıf kümesi oluşturmalısınız `BindingElement` veya `Binding` .config dosyası kullanılarak yapılandırılabilir. Bu sınıfları oluşturmak ve müşterinizin deneyimini geliştirmek için ConfigurationCodeGenerator aracını kullanabilirsiniz.  
  
### <a name="to-build-the-tool"></a>Aracı yapılandırmak için  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Bir dosya oluşturur çözümü oluşturma: ConfigurationCodeGenerator.exe. İçin sınıflar oluşturmak için bu aracı kullanmak nasıl oluşturulduğunu gösteren örnek komut satırı dosya SampleRun.cmd sahip [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
1.  Her iki özel varsa komut isteminde aşağıdaki komutu yazın `BindingElement` türünü ve özel bir `Binding` türü:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     Veya yalnızca özel varsa, aşağıdaki komutu yazın `BindingElement` türü:  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Veya yalnızca özel varsa, aşağıdaki komutu yazın `Binding` türü:  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     Komutu için üç .cs dosyaları oluşturur `BindingElement` (belirttiyseniz / olabilir: seçeneği), standart beş .cs dosyaları `Binding` (/sb belirtilmişse: seçeneği) ve bir .xml dosyası.  
  
    1.  /Be seçeneği kullanılırsa, .cs birini uygulayan dosyaları `BindingElementExtensionSection` bağlama öğesi için. Bu kodu gösterir, `BindingElement` yapılandırma sistemi için özel diğer bağlamalar bağlama öğesi kullanabilirsiniz. Diğer dosyaları Varsayılanları ve sabitleri temsil eden sınıfları içerir. Dosyalarınız `//TODO` açıklamaları, varsayılan değerleri güncelleştirmek için şu aralıklarla uyar.  
  
    2.  /Sb seçeneği belirtilmişse, iki .cs dosyaları uygulayan bir `StandardBindingElement` ve `StandardBindingCollectionElement` sırasıyla, bu, yapılandırma sistemi, standart bağlama kullanıma sunar. Diğer dosyaları Varsayılanları ve sabitleri temsil eden sınıfları içerir. Dosyalarınız `//TODO` açıklamaları, varsayılan değerleri güncelleştirmek için şu aralıklarla uyar.  
  
         /Sb belirtilmişse: CodeToAddTo seçeneği\<*YourStdBinding*> .cs sahip kodu, standart bağlama uygular sınıfına el ile eklemeniz gerekir.  
  
     SampleConfig.xml dosya önceki adımda 1 veya 2 tanımlı işleyicileri kaydeder yapılandırma dosyasının eklemelisiniz yapılandırma kodunu içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.
