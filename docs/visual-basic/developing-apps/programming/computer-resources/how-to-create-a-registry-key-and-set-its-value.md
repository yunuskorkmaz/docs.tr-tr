---
title: "Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5f60dd4723e254b0af59a7794e251a082c9a40c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama
`CreateSubKey` Yöntemi `My.Computer.Registry` nesnesi, bir kayıt defteri anahtarı oluşturmak için kullanılabilir.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-a-registry-key"></a>Bir kayıt defteri anahtarı oluşturmak için  
  
-   Kullanım `CreateSubKey` yöntemi, anahtarın adının yanı sıra anahtarı altındaki yerleştirmek için hangi hive belirtme. Parametre `Subkey` büyük küçük harfe duyarlı değildir. Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a>Bir kayıt defteri anahtarı oluşturmak ve bunu bir değer ayarlamak için  
  
1.  Kullanım `CreateSubkey` yöntemi, anahtarın adının yanı sıra anahtarı altındaki yerleştirmek için hangi hive belirtme. Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında.  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  Değeriyle ayarlamak `SetValue` yöntemi. Bu örnekte, dize değeri ayarlar. "" Test değeri olan"için MyTestKeyValue".  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, kayıt defteri anahtarı oluşturur `MyTestKey` HKEY_CURRENT_USER altında ve dize değeri ayarlar `MyTestKeyValue` için `This is a test value`.  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Anahtarınız için uygun bir konum bulmak için kayıt defteri yapısı inceleyin. Örneğin, geçerli kullanıcının HKEY_CURRENT_USER\Software anahtarını açın ve şirketinizin adı ile bir anahtar oluşturmak isteyebilirsiniz. Ardından, şirketinizin anahtarına kayıt defteri değerlerini ekleyin.  
  
 Kayıt defteri bir Web uygulamasından okurken, geçerli kullanıcının kimlik doğrulaması ve kimliğe bürünme Web uygulamasında uygulanan bağlıdır.  
  
 Kullanıcı klasörüne veri yazmak için daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) yerine yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>).  
  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir. Başka bir işlem, belki de kötü amaçlı bir değer önceden oluşturduğunuz ve buna erişiminiz. Kayıt defteri değerindeki veri geçirdiğinizde, verileri başka bir işlem mevcut değil. Bunu önlemek için kullanmak <xref:Microsoft.Win32.RegistryKey.GetValue%2A> yöntemi. Döndürdüğü `Nothing` anahtarı zaten mevcut değilse.  
  
 Kayıt defteri anahtarı, ACL'ler tarafından (erişim denetim listeleri) korumalı olsa bile düz metin olarak kayıt defterinde parolalar gibi gizli depolamak için güvenli değildir.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Kullanıcının kayıt defteri anahtarları oluşturma izni yok (<xref:System.Security.SecurityException>).  
  
-   Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).  
  
-   Anahtar kapalı (<xref:System.IO.IOException>).  
  
-   Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu işlem çalıştırmak için derleme ayrıcalık düzeyi verilen tarafından gerektiriyor <xref:System.Security.Permissions.RegistryPermission> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Benzer şekilde, kullanıcının oluşturulması veya ayarları için doğru ACL olmalıdır. Örneğin, kod erişimi güvenlik izni olan yerel bir uygulama işletim sistemi izni olmayabilir. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Kod erişim güvenliği temelleri](../../../../framework/misc/code-access-security-basics.md)
