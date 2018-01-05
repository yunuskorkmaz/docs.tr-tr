---
title: "SendMail özel etkinlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a6d0338b7c460d7053af9264527a6cd6d263673
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="76202-102">SendMail özel etkinlik</span><span class="sxs-lookup"><span data-stu-id="76202-102">SendMail Custom Activity</span></span>
<span data-ttu-id="76202-103">Bu örnek, türetilen özel bir etkinlik oluşturmak gösterilmiştir <xref:System.Activities.AsyncCodeActivity> bir iş akışı uygulama içinde kullanmak için SMTP kullanarak posta göndermek için.</span><span class="sxs-lookup"><span data-stu-id="76202-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="76202-104">Özel Etkinlik özelliklerini kullanan <xref:System.Net.Mail.SmtpClient> zaman uyumsuz olarak e-posta göndermek için ve kimlik doğrulaması ile posta göndermek için.</span><span class="sxs-lookup"><span data-stu-id="76202-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send e-mail asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="76202-105">Bırakma yolu test ve test modu, belirteç değiştirme, dosya şablonları gibi bazı son kullanıcı özellikler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="76202-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="76202-106">Aşağıdaki tabloda bağımsız değişkenleri ayrıntıları `SendMail` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="76202-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="76202-107">Ad</span><span class="sxs-lookup"><span data-stu-id="76202-107">Name</span></span>|<span data-ttu-id="76202-108">Tür</span><span class="sxs-lookup"><span data-stu-id="76202-108">Type</span></span>|<span data-ttu-id="76202-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76202-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="76202-110">Ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="76202-110">Host</span></span>|<span data-ttu-id="76202-111">Dize</span><span class="sxs-lookup"><span data-stu-id="76202-111">String</span></span>|<span data-ttu-id="76202-112">SMTP sunucusunun ana bilgisayar adresi.</span><span class="sxs-lookup"><span data-stu-id="76202-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="76202-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="76202-113">Port</span></span>|<span data-ttu-id="76202-114">Dize</span><span class="sxs-lookup"><span data-stu-id="76202-114">String</span></span>|<span data-ttu-id="76202-115">Ana bilgisayar SMTP hizmetinin bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="76202-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="76202-116">enableSsl</span><span class="sxs-lookup"><span data-stu-id="76202-116">EnableSsl</span></span>|<span data-ttu-id="76202-117">bool</span><span class="sxs-lookup"><span data-stu-id="76202-117">bool</span></span>|<span data-ttu-id="76202-118">Belirtir olup olmadığını <xref:System.Net.Mail.SmtpClient> Güvenli Yuva Katmanı (SSL) bağlantıyı şifrelemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="76202-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="76202-119">UserName</span><span class="sxs-lookup"><span data-stu-id="76202-119">UserName</span></span>|<span data-ttu-id="76202-120">Dize</span><span class="sxs-lookup"><span data-stu-id="76202-120">String</span></span>|<span data-ttu-id="76202-121">Gönderenin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için kullanıcı adı <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="76202-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="76202-122">Parola</span><span class="sxs-lookup"><span data-stu-id="76202-122">Password</span></span>|<span data-ttu-id="76202-123">Dize</span><span class="sxs-lookup"><span data-stu-id="76202-123">String</span></span>|<span data-ttu-id="76202-124">Gönderenin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için parola <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="76202-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="76202-125">Konu</span><span class="sxs-lookup"><span data-stu-id="76202-125">Subject</span></span>|<span data-ttu-id="76202-126"><xref:System.Activities.InArgument%601>\<dize ></span><span class="sxs-lookup"><span data-stu-id="76202-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="76202-127">İleti konusu.</span><span class="sxs-lookup"><span data-stu-id="76202-127">Subject of the message.</span></span>|  
|<span data-ttu-id="76202-128">Gövde</span><span class="sxs-lookup"><span data-stu-id="76202-128">Body</span></span>|<span data-ttu-id="76202-129"><xref:System.Activities.InArgument%601>\<dize ></span><span class="sxs-lookup"><span data-stu-id="76202-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="76202-130">İleti gövdesi.</span><span class="sxs-lookup"><span data-stu-id="76202-130">Body of the message.</span></span>|  
|<span data-ttu-id="76202-131">Ekler</span><span class="sxs-lookup"><span data-stu-id="76202-131">Attachments</span></span>|<span data-ttu-id="76202-132"><xref:System.Activities.InArgument%601>\<dize ></span><span class="sxs-lookup"><span data-stu-id="76202-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="76202-133">Bu e-posta iletisine verileri depolamak için kullanılan ek koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="76202-133">Attachment collection used to store data attached to this e-mail message.</span></span>|  
|<span data-ttu-id="76202-134">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="76202-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="76202-135">Bu e-posta iletisinin adresinden.</span><span class="sxs-lookup"><span data-stu-id="76202-135">From address for this e-mail message.</span></span>|  
|<span data-ttu-id="76202-136">Bitiş</span><span class="sxs-lookup"><span data-stu-id="76202-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="76202-137">Bu e-posta iletisinin alıcılarını içeren koleksiyon adres.</span><span class="sxs-lookup"><span data-stu-id="76202-137">Address collection that contains the recipients of this e-mail message.</span></span>|  
|<span data-ttu-id="76202-138">CC</span><span class="sxs-lookup"><span data-stu-id="76202-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="76202-139">Bu e-posta iletisi için gizli kopya (CC) alıcıları içeren koleksiyon adres.</span><span class="sxs-lookup"><span data-stu-id="76202-139">Address collection that contains the carbon copy (CC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="76202-140">GİZLİ</span><span class="sxs-lookup"><span data-stu-id="76202-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="76202-141">Bu e-posta iletisi için gizli kopya (gizli) alıcıları içeren koleksiyon adres.</span><span class="sxs-lookup"><span data-stu-id="76202-141">Address collection that contains the blind carbon copy (BCC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="76202-142">Belirteçler</span><span class="sxs-lookup"><span data-stu-id="76202-142">Tokens</span></span>|<span data-ttu-id="76202-143"><xref:System.Activities.InArgument%601>< IDictionary\<dize, dize >></span><span class="sxs-lookup"><span data-stu-id="76202-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="76202-144">Gövdesinde değiştirmek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="76202-144">Tokens to replace in the body.</span></span> <span data-ttu-id="76202-145">Bu özellik, kullanıcıların bu özelliği kullanan sağlanan belirteçleri tarafından daha sonra değiştirilebilir daha bazı değerler gövdesinde belirtmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="76202-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="76202-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="76202-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="76202-147">Dize</span><span class="sxs-lookup"><span data-stu-id="76202-147">String</span></span>|<span data-ttu-id="76202-148">Gövdesi için bir şablon yolu.</span><span class="sxs-lookup"><span data-stu-id="76202-148">Path of a template for the body.</span></span> <span data-ttu-id="76202-149">`SendMail` Etkinlik kendi gövde özelliğine bu dosyanın içeriğini kopyalar.</span><span class="sxs-lookup"><span data-stu-id="76202-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="76202-150">Şablon belirteçleri özelliği içeriğine göre değiştirilir belirteçleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="76202-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="76202-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="76202-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="76202-152">Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adresine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="76202-152">When this property is set, all e-mails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="76202-153">Bu özellik, iş akışları test edilirken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="76202-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="76202-154">Örneğin, emin olmak istediğinizde tüm e-postalar gerçek alıcılara göndermeden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="76202-154">For example, when you want to make sure that all e-mails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="76202-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="76202-155">TestDropPath</span></span>|<span data-ttu-id="76202-156">Dize</span><span class="sxs-lookup"><span data-stu-id="76202-156">String</span></span>|<span data-ttu-id="76202-157">Bu özellik ayarlandığında, tüm e-postalar de belirtilen dosyasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="76202-157">When this property is set, all e-mails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="76202-158">Bu özellik biçimini ve giden e-postalar içeriğini uygun olmasını sağlamak için iş akışlarını, test veya geldiğinde kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="76202-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing e-mails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="76202-159">Çözüm içeriği</span><span class="sxs-lookup"><span data-stu-id="76202-159">Solution Contents</span></span>  
 <span data-ttu-id="76202-160">Çözüm iki proje içerir.</span><span class="sxs-lookup"><span data-stu-id="76202-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="76202-161">Proje</span><span class="sxs-lookup"><span data-stu-id="76202-161">Project</span></span>|<span data-ttu-id="76202-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76202-162">Description</span></span>|<span data-ttu-id="76202-163">Önemli dosyaları</span><span class="sxs-lookup"><span data-stu-id="76202-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="76202-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="76202-164">SendMail</span></span>|<span data-ttu-id="76202-165">SendMail etkinliği</span><span class="sxs-lookup"><span data-stu-id="76202-165">The SendMail activity</span></span>|<span data-ttu-id="76202-166">1.  SendMail.cs: ana etkinlik uygulama</span><span class="sxs-lookup"><span data-stu-id="76202-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="76202-167">2.  SendMailDesigner.xaml ve SendMailDesigner.xaml.cs: SendMail etkinliğinin Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="76202-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="76202-168">3.  MailTemplateBody.htm: gönderilecek e-posta şablonu.</span><span class="sxs-lookup"><span data-stu-id="76202-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="76202-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="76202-169">SendMailTestClient</span></span>|<span data-ttu-id="76202-170">Test SendMail etkinliği istemci.</span><span class="sxs-lookup"><span data-stu-id="76202-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="76202-171">Bu proje SendMail etkinlik çağırma iki yolla gösterir: bildirimli olarak ve program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="76202-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="76202-172">1.  Sequence1.XAML: SendMail etkinlik çağıran iş akışı.</span><span class="sxs-lookup"><span data-stu-id="76202-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="76202-173">2.  Program.cs: Sıra1 çağırır ve program aracılığıyla SendMail kullanan bir iş akışı da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="76202-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="76202-174">Başka bir yapılandırma SendMail etkinliği</span><span class="sxs-lookup"><span data-stu-id="76202-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="76202-175">Aşağıdaki örnekte gösterilmese kullanıcılar SendMail etkinliğin ek yapılandırma gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="76202-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="76202-176">Sonraki üç bölümde bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="76202-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="76202-177">Gövdede belirtilen belirteçleri kullanarak bir e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="76202-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="76202-178">Bu kod parçacığını nasıl gövdesinde belirteçleri içeren e-posta gönderebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="76202-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="76202-179">Belirteçleri gövde özelliğinde nasıl sağlanır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="76202-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="76202-180">Bu belirteçler için değerler belirteçleri özelliğine sağlanır.</span><span class="sxs-lookup"><span data-stu-id="76202-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="76202-181">Bir şablonu kullanarak bir e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="76202-181">Sending an email using a template</span></span>  
 <span data-ttu-id="76202-182">Bu kod parçacığında gövdesinde bir şablon belirteçleri kullanarak bir e-posta göndermek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="76202-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="76202-183">Ayarlarken dikkat `BodyTemplateFilePath` özelliği biz gerekmez (şablon dosyası içeriğini gövdesine kopyalanacak) gövde özelliği için değer sağlayın.</span><span class="sxs-lookup"><span data-stu-id="76202-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="76202-184">Mod testinde postalar gönderme</span><span class="sxs-lookup"><span data-stu-id="76202-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="76202-185">Bu kod parçacığını iki sınama özelliklerin nasıl ayarlanacağını gösterir: ayarlayarak `TestMailTo` tüm iletileri gönderilir john.doe@contoso.con (bakmadan değerlerinin Kime, bilgi, gizli).</span><span class="sxs-lookup"><span data-stu-id="76202-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="76202-186">TestDropPath ayarlayarak tüm giden e-postalar, aynı zamanda sağlanan yolunda kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="76202-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="76202-187">Bu özellikler bağımsız olarak ayarlanabilir (bunlar birbiriyle ilgili olmayan).</span><span class="sxs-lookup"><span data-stu-id="76202-187">These properties can be set independently (they are not related).</span></span>  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="76202-188">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="76202-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="76202-189">Bu örnek için bir SMTP sunucusuna erişim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="76202-189">Access to a SMTP server is required for this sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="76202-190">bir SMTP sunucusu kurma ayarlama, aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="76202-190"> setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="76202-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="76202-191">Microsoft Technet</span></span>](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="76202-192">SMTP Hizmeti (IIS 6.0) yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76202-192">Configuring the SMTP Service (IIS 6.0)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="76202-193">IIS 7.0: SMTP e-posta yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76202-193">IIS 7.0: Configure SMTP E-Mail</span></span>](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="76202-194">SMTP hizmeti nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="76202-194">How to Install the SMTP Service</span></span>](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="76202-195">Üçüncü taraflar tarafından sağlanan SMTP Öykünücüler indirme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76202-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="76202-196">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="76202-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="76202-197">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], SendMail.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="76202-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="76202-198">Geçerli bir SMTP sunucusuna erişimi olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="76202-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="76202-199">Kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="76202-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="76202-200">Program, sunucu adresi ve Kimden ve Kime e-posta adreslerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="76202-200">Configure the program with your server address, and From and To e-mail addresses.</span></span>  
  
     <span data-ttu-id="76202-201">Bu örnek düzgün çalışması için ilk ve son e-posta adresi ve SMTP sunucusunun adresini değerini Program.cs ve Sequence.xaml yapılandırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="76202-201">To correctly run this sample, you may need to configure the value of From and To e-mail addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="76202-202">Program iki farklı şekilde posta gönderir olduğundan her iki konumda adresi değiştirmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="76202-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="76202-203">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="76202-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="76202-204">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="76202-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76202-205">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="76202-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="76202-206">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="76202-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="76202-207">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="76202-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="76202-208">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="76202-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`