---
title: SendMail Özel Etkinliği
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: b1e2d58a09362569d4d408f6e1c9e589aa6bda76
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715574"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="f0aaf-102">SendMail Özel Etkinliği</span><span class="sxs-lookup"><span data-stu-id="f0aaf-102">SendMail Custom Activity</span></span>
<span data-ttu-id="f0aaf-103">Bu örnek, bir iş akışı uygulamasında kullanmak üzere SMTP kullanarak e-posta göndermek için <xref:System.Activities.AsyncCodeActivity> türetilen özel bir etkinliğin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="f0aaf-104">Özel etkinlik, e-postayı zaman uyumsuz olarak göndermek ve kimlik doğrulamasıyla posta göndermek için <xref:System.Net.Mail.SmtpClient> yeteneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="f0aaf-105">Ayrıca, test modu, belirteç değiştirme, dosya şablonları ve test bırakma yolu gibi bazı son kullanıcı özellikleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="f0aaf-106">Aşağıdaki tabloda `SendMail` etkinliğinin bağımsız değişkenleri ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="f0aaf-107">Name</span><span class="sxs-lookup"><span data-stu-id="f0aaf-107">Name</span></span>|<span data-ttu-id="f0aaf-108">Tür</span><span class="sxs-lookup"><span data-stu-id="f0aaf-108">Type</span></span>|<span data-ttu-id="f0aaf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0aaf-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f0aaf-110">Konak</span><span class="sxs-lookup"><span data-stu-id="f0aaf-110">Host</span></span>|<span data-ttu-id="f0aaf-111">Dize</span><span class="sxs-lookup"><span data-stu-id="f0aaf-111">String</span></span>|<span data-ttu-id="f0aaf-112">SMTP sunucusu konağının adresi.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="f0aaf-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="f0aaf-113">Port</span></span>|<span data-ttu-id="f0aaf-114">Dize</span><span class="sxs-lookup"><span data-stu-id="f0aaf-114">String</span></span>|<span data-ttu-id="f0aaf-115">Konaktaki SMTP hizmetinin bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="f0aaf-116">enableSsl</span><span class="sxs-lookup"><span data-stu-id="f0aaf-116">EnableSsl</span></span>|<span data-ttu-id="f0aaf-117">bool</span><span class="sxs-lookup"><span data-stu-id="f0aaf-117">bool</span></span>|<span data-ttu-id="f0aaf-118"><xref:System.Net.Mail.SmtpClient> bağlantıyı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="f0aaf-119">UserName</span><span class="sxs-lookup"><span data-stu-id="f0aaf-119">UserName</span></span>|<span data-ttu-id="f0aaf-120">Dize</span><span class="sxs-lookup"><span data-stu-id="f0aaf-120">String</span></span>|<span data-ttu-id="f0aaf-121">Gönderenin <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliğinin kimliğini doğrulamak üzere kimlik bilgilerini ayarlamak için Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="f0aaf-122">istemcisiyle yönetilen bir cihaz için)</span><span class="sxs-lookup"><span data-stu-id="f0aaf-122">Password</span></span>|<span data-ttu-id="f0aaf-123">Dize</span><span class="sxs-lookup"><span data-stu-id="f0aaf-123">String</span></span>|<span data-ttu-id="f0aaf-124">Gönderenin <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliğini doğrulamak üzere kimlik bilgilerini ayarlamak için parola.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="f0aaf-125">Konu</span><span class="sxs-lookup"><span data-stu-id="f0aaf-125">Subject</span></span>|<span data-ttu-id="f0aaf-126"><xref:System.Activities.InArgument%601>\<dize ></span><span class="sxs-lookup"><span data-stu-id="f0aaf-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f0aaf-127">İletinin konusu.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-127">Subject of the message.</span></span>|  
|<span data-ttu-id="f0aaf-128">bölümü</span><span class="sxs-lookup"><span data-stu-id="f0aaf-128">Body</span></span>|<span data-ttu-id="f0aaf-129"><xref:System.Activities.InArgument%601>\<dize ></span><span class="sxs-lookup"><span data-stu-id="f0aaf-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f0aaf-130">İletinin gövdesi.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-130">Body of the message.</span></span>|  
|<span data-ttu-id="f0aaf-131">Ekler</span><span class="sxs-lookup"><span data-stu-id="f0aaf-131">Attachments</span></span>|<span data-ttu-id="f0aaf-132"><xref:System.Activities.InArgument%601>\<dize ></span><span class="sxs-lookup"><span data-stu-id="f0aaf-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f0aaf-133">Bu e-posta iletisine eklenen verileri depolamak için kullanılan ek koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="f0aaf-134">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="f0aaf-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="f0aaf-135">Bu e-posta iletisinin Kimden adresi.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-135">From address for this email message.</span></span>|  
|<span data-ttu-id="f0aaf-136">Bitiş</span><span class="sxs-lookup"><span data-stu-id="f0aaf-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f0aaf-137">Bu e-posta iletisinin alıcılarını içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="f0aaf-138">CC</span><span class="sxs-lookup"><span data-stu-id="f0aaf-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f0aaf-139">Bu e-posta iletisi için karbon kopyası (CC) alıcılarını içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="f0aaf-140">ALÝCÝ</span><span class="sxs-lookup"><span data-stu-id="f0aaf-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f0aaf-141">Bu e-posta iletisi için gizli bilgi kopyası (gızlı) alıcılarını içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="f0aaf-142">Belirteçler</span><span class="sxs-lookup"><span data-stu-id="f0aaf-142">Tokens</span></span>|<span data-ttu-id="f0aaf-143"><xref:System.Activities.InArgument%601>< IDictionary\<dize, dize > ></span><span class="sxs-lookup"><span data-stu-id="f0aaf-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="f0aaf-144">Gövdede değiştirilecek belirteçler.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-144">Tokens to replace in the body.</span></span> <span data-ttu-id="f0aaf-145">Bu özellik, kullanıcıların gövdede daha sonra bu özellik kullanılarak girilen belirteçlerle değiştirilebilmesi için bazı değerler belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="f0aaf-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="f0aaf-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="f0aaf-147">Dize</span><span class="sxs-lookup"><span data-stu-id="f0aaf-147">String</span></span>|<span data-ttu-id="f0aaf-148">Gövde şablonunun yolu.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-148">Path of a template for the body.</span></span> <span data-ttu-id="f0aaf-149">`SendMail` etkinliği bu dosyanın içeriğini Body özelliğine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="f0aaf-150">Şablon, belirteçler özelliğinin içeriğiyle değiştirilmiş belirteçleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="f0aaf-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="f0aaf-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="f0aaf-152">Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adrese gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="f0aaf-153">Bu özellik iş akışlarını test ederken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="f0aaf-154">Örneğin, tüm e-postaların gerçek alıcılara gönderilmeksizin gönderilmesini sağlamak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="f0aaf-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="f0aaf-155">TestDropPath</span></span>|<span data-ttu-id="f0aaf-156">Dize</span><span class="sxs-lookup"><span data-stu-id="f0aaf-156">String</span></span>|<span data-ttu-id="f0aaf-157">Bu özellik ayarlandığında, tüm e-postalar da belirtilen dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="f0aaf-158">Bu özellik, giden e-postaların biçiminin ve içeriğinin uygun olduğundan emin olmak için iş akışlarını test ederken veya hata ayıklarken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="f0aaf-159">Çözüm Içeriği</span><span class="sxs-lookup"><span data-stu-id="f0aaf-159">Solution Contents</span></span>  
 <span data-ttu-id="f0aaf-160">Çözüm iki proje içerir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="f0aaf-161">{1&gt;Proje (Project)&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f0aaf-161">Project</span></span>|<span data-ttu-id="f0aaf-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0aaf-162">Description</span></span>|<span data-ttu-id="f0aaf-163">Önemli dosyalar</span><span class="sxs-lookup"><span data-stu-id="f0aaf-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="f0aaf-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="f0aaf-164">SendMail</span></span>|<span data-ttu-id="f0aaf-165">SendMail etkinliği</span><span class="sxs-lookup"><span data-stu-id="f0aaf-165">The SendMail activity</span></span>|<span data-ttu-id="f0aaf-166">1. SendMail.cs: ana etkinlik için uygulama</span><span class="sxs-lookup"><span data-stu-id="f0aaf-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="f0aaf-167">SendMail etkinliği için 2. SendMailDesigner. xaml ve SendMailDesigner.xaml.cs: Designer</span><span class="sxs-lookup"><span data-stu-id="f0aaf-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="f0aaf-168">3. MailTemplateBody. htm: gönderilecek e-postanın şablonu.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="f0aaf-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="f0aaf-169">SendMailTestClient</span></span>|<span data-ttu-id="f0aaf-170">SendMail etkinliğini test etmek için istemci.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="f0aaf-171">Bu proje, SendMail etkinliğini çağırmanın iki yolunu gösterir: bildirimli ve programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="f0aaf-172">1. Sequence1. xaml: SendMail etkinliğini çağıran iş akışı.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="f0aaf-173">2. Program.cs: Sequence1 çağırır ve ayrıca SendMail kullanan programlı bir iş akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="f0aaf-174">SendMail etkinliğinin daha fazla yapılandırması</span><span class="sxs-lookup"><span data-stu-id="f0aaf-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="f0aaf-175">Örnekte gösterilmese de, kullanıcılar SendMail etkinliğinin ek yapılandırmasını gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="f0aaf-176">Sonraki üç bölümde bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="f0aaf-177">Gövdede belirtilen belirteçleri kullanarak e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="f0aaf-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="f0aaf-178">Bu kod parçacığı, gövdedeki belirteçlerle nasıl e-posta gönderebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="f0aaf-179">Gövde özelliğinde belirteçlerin nasıl sağlandığını fark edin.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="f0aaf-180">Bu belirteçlerin değerleri belirteçler özelliğine sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="f0aaf-181">Şablon kullanarak e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="f0aaf-181">Sending an email using a template</span></span>  
 <span data-ttu-id="f0aaf-182">Bu kod parçacığında, gövdedeki bir şablon belirteçlerini kullanarak e-posta gönderme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="f0aaf-183">`BodyTemplateFilePath` özelliği ayarlanırken Body özelliği için değer sağlamak zorunda olduğumuz (şablon dosyasının içeriği gövdeye kopyalanacak) olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="f0aaf-184">Sınama modunda postaları gönderme</span><span class="sxs-lookup"><span data-stu-id="f0aaf-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="f0aaf-185">Bu kod parçacığı, iki test özelliği ayarlamayı gösterir: tüm iletiler için `TestMailTo` ayarlayarak, `john.doe@contoso.con` (Kime, CC, gizli değer olmadan) gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="f0aaf-186">TestDropPath ' i ayarlayarak tüm giden e-postalar da, belirtilen yola kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="f0aaf-187">Bu özellikler bağımsız olarak ayarlanabilir (ilişkili değildir).</span><span class="sxs-lookup"><span data-stu-id="f0aaf-187">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="f0aaf-188">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f0aaf-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="f0aaf-189">Bu örnek için bir SMTP sunucusuna erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="f0aaf-190">SMTP sunucusu kurma hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- [<span data-ttu-id="f0aaf-191">Microsoft TechNet</span><span class="sxs-lookup"><span data-stu-id="f0aaf-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [<span data-ttu-id="f0aaf-192">SMTP hizmetini yapılandırma (IIS 6,0)</span><span class="sxs-lookup"><span data-stu-id="f0aaf-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [<span data-ttu-id="f0aaf-193">IIS 7,0: SMTP e-postasını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f0aaf-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [<span data-ttu-id="f0aaf-194">SMTP hizmetini nasıl yükleyeceğiniz</span><span class="sxs-lookup"><span data-stu-id="f0aaf-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="f0aaf-195">Üçüncü taraflar tarafından sağlanan SMTP öykünücüleri indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="f0aaf-196">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f0aaf-196">To run this sample</span></span>  
  
1. <span data-ttu-id="f0aaf-197">Visual Studio 2010 kullanarak SendMail. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="f0aaf-198">Geçerli bir SMTP sunucusuna erişiminiz olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="f0aaf-199">Bkz. kurulum yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-199">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="f0aaf-200">Programı sunucu adresinizle ve Kimden e-posta adreslerinden yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="f0aaf-201">Bu örneği doğru bir şekilde çalıştırmak için, ' ın ve e-posta adresleri ve Program.cs içindeki SMTP sunucusunun adresi ve dizi. xaml içindeki adresini yapılandırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="f0aaf-202">Program postayı iki farklı şekilde gönderdiğinden, her iki konumdaki adresi de değiştirmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="f0aaf-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="f0aaf-203">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="f0aaf-204">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f0aaf-205">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f0aaf-206">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-206">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f0aaf-207">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0aaf-208">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f0aaf-208">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
